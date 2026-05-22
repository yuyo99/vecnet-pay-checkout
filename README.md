# Vecnet Pay — Hosted Checkout V2 (Prototype)

Static, self-contained HTML/CSS/JS prototype of the Vecnet Pay hosted-checkout
V2 design. Demonstrates the white-card preview, card flip, brand detection
(Visa / Mastercard / Amex), method tabs (Tarjeta / SPEI / OXXO / Tienda),
mobile collapsible summary + sticky CTA, expiry validation, and the success
flow.

## Files

- `index.html` — the entire prototype (HTML + CSS + JS inline, no build step)
- `vercel.json` — static deploy config with basic security headers

## Deploy

Vercel auto-detects this as a static site. Import the repo into a new project
and deploy with default settings — no environment variables required.

## Local preview

```bash
# Any static server works
python3 -m http.server 8000
# or
npx serve .
```

Then open <http://localhost:8000/>.

## What lives where

Branding marks (Visa, Mastercard, Amex, SEP, OXXO) are inline SVGs in the
prototype — the production build should swap them for licensed assets.
