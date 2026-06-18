# kylefolio

A single-page retro/90s-web personal portfolio — marquees, scanlines, a guestbook, theme switcher, and a fake terminal you can `ssh` into. No build step for the page itself: it's plain HTML that ships straight to GitHub Pages.

👉 Live at [kylemeister.dev](https://kylemeister.dev)

## Layout

```
src/
  index.html    the whole site (markup + inline styles + DC components)
  support.js    the "dc-runtime" — a small React-based component runtime (generated, do not hand-edit)
  CNAME         custom domain for GitHub Pages
  uploads/      images (profile pic, etc.)
.github/workflows/deploy.yml   auto-deploy to GitHub Pages on push to main
```

`index.html` is organized into clearly-commented sections — `BANNER`, `MARQUEE`, `NAV`, `ABOUT`, `PROJECTS`, `SOCIALS`, `GUESTBOOK`, `THEME SELECTOR`, `FOOTER`, and the `TERMINAL OVERLAY`. Search for `===== SECTION =====` to jump around.

## Running locally

It's static — just serve the `src/` folder with anything:

```bash
cd src
python -m http.server 8000   # then open http://localhost:8000
```

Or open `src/index.html` directly in a browser (a local server is nicer so fonts/paths resolve cleanly).

## Make it your own

1. Edit `src/index.html` — swap the name in the `BANNER`, rewrite the `ABOUT`, `PROJECTS`, and `SOCIALS` sections, and drop your own images into `src/uploads/`.
2. Tweak colors via the CSS variables (`--c-accent`, `--c-text`, `--c-rgb`, …) — the theme selector swaps these at runtime.
3. Have fun with the easter eggs: the Konami code and the `ssh kyle@kylemeister.dev` terminal command both live in `index.html` / `support.js`.

> ⚠️ `support.js` is generated from a separate `dc-runtime` (TypeScript) project — don't edit it by hand; it gets overwritten on rebuild.

## Deploy

Pushing to `main` triggers `.github/workflows/deploy.yml`, which uploads `src/` and publishes it to GitHub Pages. To set this up on a fresh fork:

1. **Repo → Settings → Pages → Build and deployment → Source: GitHub Actions.**
2. Push to `main`. The workflow builds and deploys automatically (watch it under the **Actions** tab).

That's the entire pipeline — no node_modules, no build, just static files.

### Custom domain

1. Put your domain in `src/CNAME` (one line, e.g. `kylemeister.dev`). It gets shipped with the site.
2. At your DNS provider, point the domain at GitHub Pages:
   - **Apex** (`example.com`): `A` records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - **Subdomain** (`www.example.com`): `CNAME` → `<your-username>.github.io`
3. In **Settings → Pages**, enter the domain and tick **Enforce HTTPS** once the cert provisions.

DNS can take a bit to propagate. Once it does, you're live. ✦

---

*powered by coffee and Claude tokens*
