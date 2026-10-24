---
name: idea-kill-search
description: Kill a business or product idea in one hour instead of three months, using three searches and four checks that catch the problems competitor research misses. Use this whenever someone is weighing up, pitching, comparing or "just thinking about" a business idea, app idea, side project or new product — including when they're already excited and only want help building it, and including when they ask "is this a good idea?", "has anyone done this?", "should I build X?" or describe a problem they want to solve for money.
---

# Kill the idea in an hour

The point of this first hour isn't to decide whether to build. It's to find the
reason not to, fast. Ideas that survive an hour of this have earned the next step.

An hour here often saves three months of building. Worth doing even when the
person is already sure.

## How to go about it

You're not trying to shoot the idea down. You're trying to find out cheaply
whether the hard part of this business is something they can actually do. Say
what you find plainly, including when the idea survives.

Two things to watch in yourself:

- **Don't soften it.** Turning "a regulator banned this" into "something to keep
  an eye on" wastes the whole exercise. If it's dead, say it's dead.
- **Don't rescue it.** Suggesting "you could do it as a managed service with
  inspectors on the ground" usually swaps in a different, harder business. If you
  want to suggest a pivot, call it a new idea and run it through the checks again.

## Step 1 — three searches

**First, work out where.** The regulation search is useless without a
jurisdiction, and most people describe an idea without naming one — "my city",
"here", "back home". Ask before searching. Guessing wastes a search and can send
you to the wrong country's rules entirely.

If they genuinely operate in more than one market, run the regulation search for
each. The answer often differs.

Then run all three. They catch different things.

| Search | What it catches |
|---|---|
| `<idea> competitors pricing` | Someone already does this, and what they charge |
| `<idea> free alternative` | Someone already does this for free |
| `<idea> regulation <current year>` | A regulator or platform has made it impossible |

The third one is the one people skip, and it kills ideas the other two never
would. A rule change can make a working business unbuildable overnight, and it
leaves no competitors behind to warn you — they all quit.

If there's a good free alternative, the idea is usually dead. "Mine will be
better" isn't a finding, it's a hope. Ask what would actually make someone switch
from free, and whether that thing can be copied.

## Step 2 — four checks

Run these even when the searches come back clean.

### Who owns the pipe, and would they build this themselves?

If the product depends on a platform — a messaging app, an app store, a payment
processor, a bank regulator, someone's API — then that platform can change the
economics whenever it likes, and often ships the same feature free. A solo founder
sitting downstream of a big platform is renting their business model.

**Count them — they stack.** One idea can sit under three owners at once: a
physical gatekeeper (an airport, a venue, a landlord), a platform that already
does the matching, and a payment rail with its own licensing. Each can kill it
on its own. When you find one owner, keep looking for the others.

Ideas with **nobody in between the founder and the customer** are worth more than
they look. Weight this heavily — closer to disqualifying than to a deduction.

If the same kill reason keeps coming up across someone's ideas, that pattern is
the finding. Screen on it *first*, before any searching, and save the hour.

### Is the hard part the code?

Ask what has to go right for a customer to be happy. If the answer involves
trusted people in physical places — inspectors, carers, drivers, warehouse staff —
this is an operations business with software bolted on. The software is the easy
10%.

That doesn't mean it can't work. It means it's a different business than they
think they're starting, with different skills, different money and none of the
margins.

### What's actually the bottleneck?

For most people weighing up ideas, the bottleneck is **talking to customers, not
coming up with ideas**. Someone with five promising ideas and no customer
conversations doesn't need a sixth. If that's the pattern, say so.

### What have they already got live?

Something already built and shipped but never marketed will usually beat starting
a new zero. Marketing a thing that exists is a shorter path to money than building
a thing that doesn't. If that applies, say it straight rather than judging the new
idea on its own.

## Step 3 — the verdict

**Dead or Parked?** Use this: *could the blocker plausibly change, and would you
know if it did?*

- A rule, a licence, a gatekeeper's policy → **Dead**. These rarely move and
  waiting isn't a plan.
- Missing money, missing data, missing a partner, bad timing → **Parked**, with
  the unblocking condition written down.
- **The full-scale version already existed and died** → Dead, and it's the
  strongest kill there is. Always search for it: the market tested this at full
  funding and the answer came back.

Pick one, in a sentence, before you explain anything:

- **Dead** — and what killed it
- **Parked** — alive but stuck on something specific, and what would unstick it
- **Live** — survived everything, plus the one assumption worth testing next

For anything not dead, name **the cheapest next test** — something that could
still kill it, doable this week, without building.

For something you called dead, offer a **disproof** instead: the cheapest thing
that would prove you wrong, and what you expect to happen. "Hand-match five of
these for free this week — I expect you won't fill five" costs nothing, respects
that you might be wrong, and usually settles it in days. It's not a rescue plan:
no building, no pivot.

## Write the verdict down

Ideas come back. The same one, or its cousin, turns up in a few months with the
enthusiasm reset. Write down the decision and **the reason** — "killed by the
central bank's single-principal rule in April" is reusable. "Didn't seem great"
isn't.

Keep one file for this, somewhere you'll find it again. If they already keep
project notes, append there. If not, make `idea-log.md` in the working folder
and say that's where it lives — "write it down" with no location quietly becomes
nothing.

```
## <idea, one line>            <date>
Verdict: Dead | Parked | Live
Killed by / blocked on: <the specific thing>
Searches that mattered: <which, and what came back>
```

Check new ideas against the list before searching. If the same kill reason keeps
showing up, that pattern is worth more than killing the tenth version of it —
say so plainly instead of running the hour again.

## Example

**Idea:** an app that reconciles card-machine payouts for small shops.

- `competitors pricing` → a few, all enterprise-priced. Looks like a gap.
- `free alternative` → the machine vendors give basic statements free. Weakens it.
- `regulation <year>` → **the central bank now requires each merchant to work
  through a single principal.** The data the product needs isn't available to a
  third party any more.

**Dead, on the third search.** Note that the first two made it look fine.
Competitor research alone would have green-lit three months of work.
