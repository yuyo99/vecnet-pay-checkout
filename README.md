# Vecnet Pay — Hosted Checkout V2 (Prototype)

Static, self-contained HTML/CSS/JS prototype of the **Vecnet Pay** hosted-checkout
V2 design, plus a **Tonder**-branded twin (BC.GAME demo) under `/tonder/`.

Demonstrates white-card preview with brand detection (Visa/Mastercard/Amex),
two checkout layouts (tabs vs. government-style cards), live merchant admin
with font + color + layout controls, card flip + 3-D Secure modal, saved cards
with CVV-only re-pay, mobile collapsible summary + sticky CTA, expiry
validation, decline + approve flows, and a print-optimized A4 receipt.

## Live URLs

| Surface | Vercel (primary) | GitHub Pages |
| --- | --- | --- |
| Vecnet checkout | <https://vecnet-pay-checkout.vercel.app/> | <https://yuyo99.github.io/vecnet-pay-checkout/> |
| Vecnet admin | <https://vecnet-pay-checkout.vercel.app/admin> | <https://yuyo99.github.io/vecnet-pay-checkout/admin.html> |
| Tonder checkout | <https://vecnet-pay-checkout.vercel.app/tonder> | <https://yuyo99.github.io/vecnet-pay-checkout/tonder/> |
| Tonder admin | <https://vecnet-pay-checkout.vercel.app/tonder/admin> | <https://yuyo99.github.io/vecnet-pay-checkout/tonder/admin.html> |

> Vercel uses clean URLs (`/admin`). GitHub Pages serves filesystem paths (`/admin.html`).

## Quick demos

- **Cards-layout (gov-style)** — pass `?layout=cards`, optionally set a hero band:

  <https://vecnet-pay-checkout.vercel.app/?layout=cards&heroBg=%237B1E3A&heroTitle=Pago+en+L%C3%ADnea&heroSub=Seleccione+su+m%C3%A9todo+de+pago+preferido+para+continuar.&heroDec=circle>

- **Single-method deep-link** — pass `?method=card` (or `spei` / `oxxo` / `tienda`)
  to hide the tab strip and jump straight to one method.

- **Demo card outcomes** — number ending `0002` → declined, `0119` → insufficient
  funds, anything else valid → approved.

- **Seed saved cards** — append `?seedDemo=cards` to see the returning-user UI.

## Layout

- `index.html` — Vecnet Pay checkout (single file: HTML + CSS + JS inline)
- `admin.html` — Vecnet merchant admin (configures brand, colors, layout,
  hero band, secondary mark, methods — persists to `localStorage`,
  live-previews via `postMessage`)
- `receipt.html` — print-optimized A4 receipt; hydrates from `sessionStorage`
- `tonder/` — same product, Tonder-branded twin (BC.GAME demo merchant)
- `vercel.json` — static config with security headers (`X-Frame-Options:
  SAMEORIGIN` so the admin iframe works)

## Deploy

**Vercel:** auto-deploys from `main` on every push. No env vars.

**GitHub Pages:** serves the same `main` branch root. The HTMLs include a
tiny `__PAGES_BASE` shim that resolves asset paths under the
`/vecnet-pay-checkout/` project prefix so the Tonder logo + receipt links
work on both hosts.

## Local preview

```bash
python3 -m http.server 8000
# or
npx serve .
```

Then open <http://localhost:8000/>.

## Production notes

Branding marks (Visa, Mastercard, Amex, SEP eagle, BC.GAME shield) are inline
SVGs in the prototype — the real Vecnet Pay V2 should swap them for licensed
assets and ship through Skyflow tokenization per the PCI requirements in
`CLAUDE.md`.
