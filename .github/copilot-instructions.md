# Copilot Instructions — Almendra (static template)

## Quick summary ✅
- This is a small **static Bootstrap template** (HTML, CSS, JS). No package.json, no test suite, and no build system checked in.
- Sources: final CSS in `css/`, SCSS sources in `scss/` (Bootstrap + partials), vendor JS/CSS in `lib/`, custom JS in `js/main.js`, and the pages at root (`index.html`, `about.html`, etc.).

## Objectives for an AI contributor 🤖
- Make small, safe edits to templates (copying patterns used in `index.html`).
- If changing styles globally, prefer editing SCSS and compiling to `css/bootstrap.min.css` or `css/style.css` and include the compiled output.
- Preserve author attribution in the footer unless license/permission allows removal (`LICENSE.txt` and footer comment in `index.html`).

## Key files & patterns (look here first) 🔎
- `index.html` — canonical page structure and examples of patterns used site-wide (carousel, product grid, tabbed product filters).
- `js/main.js` — custom behavior: spinner removal, WOW animations, back-to-top, and OwlCarousel initialization. Keep jQuery usage/order in mind.
- `css/style.css` — site-specific overrides and the final styling loaded after Bootstrap.
- `scss/` — Bootstrap source and partials for advanced theming. Recompile SCSS when updating variables or Bootstrap styles.
- `lib/` — third-party libraries (WOW, OwlCarousel, easing, waypoints). Update by replacing entire subfolders; avoid patching minified vendor files directly.
- `img/` — image assets referenced by relative paths; update references in HTML when adding images.

## How to run locally / test changes 🧪
1. Start a simple HTTP server in the repo root (Windows example):
   - `python -m http.server 8000` and open `http://localhost:8000`
   - or use `npx http-server` if available.
2. Verify script order in the page footer: jQuery → Bootstrap bundle → third-party libs → `js/main.js`.
3. For style changes using SCSS, compile locally (Dart Sass recommended):
   - `sass scss/bootstrap.scss css/bootstrap.min.css --style=compressed` (adjust paths if needed)
   - Or edit `css/style.css` for quick tweaks (remember it is loaded after `bootstrap.min.css`).

## Examples of common changes (copy/paste patterns) ✂️
- Add a new product card: replicate one `.product-item` block in `index.html` and add image to `img/`.
- Change animation timing: edit `data-wow-delay` on elements with `wow` classes (e.g., `data-wow-delay="0.3s"`).
- Initialize a new carousel: follow the `testimonial-carousel` pattern in `js/main.js` (uses `.owlCarousel({...})`).

## Debugging tips 🔧
- If interactive features fail: open DevTools Console — most issues are missing/misordered scripts or jQuery version mismatches.
- For CSS changes not showing: ensure browser cache is cleared or use querystring (e.g., `css/style.css?v=1`) while testing.

> Important: This template requires leaving the footer attribution unless you have a license or the credit removal permission (see the comment in `index.html` and `LICENSE.txt`).

## PR & contribution guidance ✨
- Keep edits scoped and include a short preview screenshot for visual changes.
- If you modify SCSS, include the compiled CSS in the PR (or provide a build step and compiled outputs) so reviewers can see resulting styling.
- Avoid changing files under `lib/` except to swap in new upstream releases (replace subfolder, update initialization if required).

---

If you'd like, I can merge this into an existing instructions file (if one exists) or add brief examples for any part you want expanded — which area should I improve next? 💬