# aquir.ai — homepage

Static marketing homepage for **Aquir**, the deal-strategy platform for revenue teams.

- **Stack:** plain HTML + CSS + a few lines of vanilla JS. **No build step.**
- **Fonts:** Plus Jakarta Sans (display) + DM Sans (body), loaded from Google Fonts.
- **Brand:** warm paper canvas + lime accent; the Decide → Position → Respond → Learn
  framework uses the product's own step colors.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole page. |
| `styles.css` | All styling and animation. |
| `CNAME` | Custom domain for GitHub Pages (`aquir.ai`). |

## Preview locally

No tooling required — open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8080   # then visit http://localhost:8080
```

## Deploy to GitHub Pages

1. Create a repo (e.g. `pbajaria/aquir-home`) and push this directory.
2. **Settings → Pages** → *Deploy from a branch* → `main` / `/ (root)`.
3. The `CNAME` file sets the custom domain to `aquir.ai`; enable **Enforce HTTPS**
   once the cert is issued.
4. Repoint DNS in Google Cloud DNS (this is a **Tier 2 / Platform Operator** change —
   it touches the live prod apex, so it needs explicit approval before running):
   - `aquir.ai` **A** → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `www.aquir.ai` **CNAME** → `pbajaria.github.io`
5. After DNS verifies and the page serves from GitHub, cancel the Squarespace
   **site plan** (not the domain — registration is prepaid to 2028).

> Current Squarespace apex records (captured for rollback):
> A `198.185.159.144`, `198.185.159.145`, `198.49.23.144`, `198.49.23.145`; `www` CNAME `ext-sq.squarespace.com`.

## Editing content

Copy lives directly in `index.html` (hero, the four framework steps, the value cards,
the persona rows, and the CTA). Colors, type, and spacing are CSS variables at the top
of `styles.css`.
