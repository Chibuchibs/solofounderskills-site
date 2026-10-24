# Deploying this site

Three things to replace before it goes live. All are literal placeholder strings,
so a find-and-replace does it:

| Placeholder | Replace with |
|---|---|
| `solofounderskills.com` | your domain, no protocol — e.g. `skills.example.com` |
| `REPLACE-WITH-YOUR-STRIPE-LINK` | your Stripe payment link |
|  `$49` | your price, if different (appears in 3 places + the JSON-LD + build-site.py) |

```bash
cd site
grep -rl 'solofounderskills.com' . | xargs sed -i '' 's|solofounderskills.com|skills.example.com|g'
grep -rl 'REPLACE-WITH-YOUR-STRIPE-LINK' . | xargs sed -i '' 's|REPLACE-WITH-YOUR-STRIPE-LINK|https://buy.stripe.com/xxx|g'
grep -rn 'REPLACE-WITH' . || echo 'all placeholders replaced'
```

## Then deploy

Static files, no build step. Same GitHub Pages flow as any other static site:
push the `site/` contents to a repo, enable Pages, point the domain at it.

The `static-host-migration` skill in this pack covers the DNS and certificate
side if the domain is already carrying email.

## After it's live

Run the checks from the `seo-foundation-audit` skill against the real domain:

```bash
for p in / /free/randomness-correctness/ /free/idea-kill-search/; do
  printf '%-34s %s\n' "$p" "$(curl -s -o /dev/null -w '%{http_code}' https://YOURDOMAIN$p)"; done
curl -s -o /dev/null -w 'robots  %{http_code}\n'  https://YOURDOMAIN/robots.txt
curl -s -o /dev/null -w 'sitemap %{http_code}\n'  https://YOURDOMAIN/sitemap.xml
curl -s -o /dev/null -w 'ogimage %{http_code}\n'  https://YOURDOMAIN/og-card.png
curl -s -o /dev/null -w 'http -> %{http_code} %{redirect_url}\n' http://YOURDOMAIN
```

Then verify in Search Console and submit the sitemap.

## Delivery after payment

Stripe payment links can redirect to a success URL after checkout. Point that at
an unlisted page holding the zip. It isn't airtight — a shared link works for
anyone — but it's proportionate for a $49 product, and the alternative is
building accounts nobody wants.

## Rebuilding the free pages

`build-site.py` generates them from the real `SKILL.md` files, so the site can't
drift from the product. Re-run it after editing either free skill:

```bash
python3 build-site.py
```
