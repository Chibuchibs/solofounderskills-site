---
name: randomness-correctness
description: Catch shuffles, random picks and odds that aren't as fair as they look, and test distributions properly. Use this whenever code shuffles an array, randomises quiz answers or options, picks a random subset, assigns odds, generates loot or rewards, or when someone says results "feel rigged", "always picks the same", or asks how to shuffle or randomise something.
---

# The shuffle that isn't

The most common randomisation bug in JavaScript:

```js
const shuffled = items.sort(() => Math.random() - 0.5);   // WRONG
```

It looks fine and it's everywhere. It is not a shuffle. Sort comparators are
expected to be consistent, and this one isn't, so the engine's sort produces
skewed permutations.

**Measured on four quiz options:**

| Position | Chance the correct answer lands there |
|---|---|
| 0 | 28.3% |
| 1 | 28.2% |
| 2 | 24.7% |
| 3 | 18.8% |

Uniform would be 25% each. In practice, always guessing the first option beat
guessing at random — a player who noticed would have an edge, and the quiz was
quietly unfair.

## The fix

Fisher–Yates, once, in a helper:

```js
function shuffle(a) {
  const out = [...a];
  for (let i = out.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [out[i], out[j]] = [out[j], out[i]];
  }
  return out;
}
```

Then replace every site. The bug usually appears more than once — one codebase
had it in **eleven** places: shuffling quiz options, picking which questions
appeared, choosing which items were offered, ordering menu choices. Each one
skewed something slightly.

**Don't blanket-replace on a pattern match.** `(Math.random() - 0.5)` also shows
up legitimately as noise in physics and jitter:

```js
velocity += (Math.random() - 0.5) * 0.012;   // leave this alone
```

Check each hit is actually a sort comparator.

## Test the distribution

Don't eyeball randomness. Count it:

```js
const pos = [0,0,0,0], N = 200000;
for (let i = 0; i < N; i++) {
  const order = shuffle(['a','b','c','d'].map((t,i) => [t,i]));
  pos[order.findIndex(o => o[1] === 0)]++;
}
pos.forEach((c,i) => console.log(i, (c/N*100).toFixed(1) + '%'));
```

Spread above about 3 percentage points across positions means something's biased.

**Use a proper generator for the test.** A hand-rolled linear congruential
generator produced 1–2 point "errors" that looked like a real bug but were the
test's own fault. `Math.random()` is uniform enough for checking distributions —
save the custom generator for when you need reproducible seeds, and validate it
separately.

## Check the odds you show people

If you display odds anywhere — a percentage, a progress bar, a chance of success
— make sure they match what the code actually rolls. Simulate the real roll a few
hundred thousand times and compare:

```
cred   0  shown 5.0%/40.0%/55.0%   actual 5.0%/40.0%/55.0%
cred 100  shown 40.0%/40.0%/20.0%  actual 40.0%/40.1%/20.0%
```

Worst error under half a percentage point means the display isn't lying. A shown
probability that the outcome doesn't honour is worse than showing nothing,
because people make decisions on it.

## While you're in there

Check that a stated goal is actually reachable. A counter reading "3 of 5" tells
players 5 is the target; if 5 happens 0.17% of the time, the interface is
promising something that effectively never happens. Work out the real odds of
every milestone you display.
