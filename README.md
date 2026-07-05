# aquir.ai — homepage

Static, single-page marketing site for **Aquir** — deal strategy intelligence for
revenue teams. Live at **https://aquir.ai** (GitHub Pages).

- **Stack:** plain HTML + CSS + a few lines of vanilla JS. **No build step.**
- **Font:** Google **Public Sans** (300 / 500 / 700).
- **Palette:** `#152316` (ink / footer / text) · `#244224` (buttons) · `#ECF7D9`
  (hero base + cream text) · `#F2EDE9` (page fallback).
- **Sections:** hero (animated CSS "blob" background with a pause/play toggle that
  respects `prefers-reduced-motion`) + dark footer. Nothing in between.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole page + inline JS (toggle, form submit). |
| `styles.css` | All styling and the blob animation. |
| `CNAME` | Custom domain for GitHub Pages (`aquir.ai`). Managed by GitHub — don't delete. |

## Preview locally

```bash
python3 -m http.server 8080   # then visit http://localhost:8080
```

## Signups (Web3Forms)

The "Request Early Access" form POSTs (AJAX) to **Web3Forms**, which emails each
submission to the registered inbox. Details:

- The `access_key` in `index.html` is **public by design** (Web3Forms scopes it to
  one destination inbox) — safe to commit.
- A hidden `botcheck` honeypot filters bots; the JS shows an inline confirmation on
  success and a fallback ("email hello@aquir.ai") on failure.
- **To change where signups are delivered:** do it in the Web3Forms dashboard
  (form → Settings → recipient email) — no code change here.
- Free tier covers a few hundred submissions/month.

## Hosting / DNS

Already live on GitHub Pages (repo Pages → `main` / root, custom domain `aquir.ai`,
HTTPS enforced). DNS is managed in the **Squarespace** domain panel; the apex `A`
records point at GitHub Pages (`185.199.108–111.153`) and `www` → `pbajaria.github.io`.
See the devops workspace change records (`changes/2026-07-05-aquir-home-*`) for the
full cutover + rollback values.

## Editing content

All copy lives in `index.html` (headline, subheading, footer). Colors, type, radii,
and the blob animation are CSS variables at the top of `styles.css`.
