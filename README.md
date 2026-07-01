# Decade Hair Design (DHD)

The homepage for **Decade Hair Design**, a black-and-white editorial hair salon by stylist **Nat Lewis**. This repository hosts the deployed static site plus the studio's original brand photography and video.

**Live site:** https://kirans0615.github.io/Decade-Hair/

## What's in this repo

- `index.html`, `assets/` — the production build of the site (compiled HTML/CSS/JS, fonts, and every image/video the page uses).
- `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png` — the DHD monogram favicon.
- `.nojekyll` — disables GitHub Pages' Jekyll processing so files/folders like `assets/` are served as-is.
- The original raw brand assets uploaded by the studio (haircut/styling photos, product photos, and the hero video, e.g. `7626891-hd_1920_1080_25fps.mp4`) — kept at the repo root as source material; the site itself uses re-encoded/renamed copies of these under `assets/`.

## Tech stack

The site is built with:

- **React 18** + **TypeScript**
- **Vite** (build tooling)
- **Tailwind CSS v3** (monochrome design-token system)
- **Framer Motion** (scroll reveals, stagger animations, parallax, magnetic cursor)
- **Lenis** (smooth scrolling)
- **lucide-react** (icons)

It's a single-page, black-and-white editorial homepage: a full-bleed autoplay video hero, an about/studio section, a services list, a bento-grid gallery with a keyboard-navigable lightbox, a small products showcase, an interior "atmosphere" section, an auto-advancing testimonials carousel, a booking CTA band, and a footer — all with `prefers-reduced-motion`-aware animation throughout.

## Running the source locally

The editable React/TypeScript source is maintained in a separate development project (not included in this repo, which holds only the deployed static output and brand assets). To work on the source: it's a standard Vite project — `npm install`, then `npm run dev` for a local dev server, `npm run typecheck` and `npm run build` to verify and produce a production build.

## How it's built and deployed

1. `vite.config.ts` sets `base: "./"` so every build-time asset reference (JS/CSS/HTML) resolves as a **relative** path.
2. The site's own asset manifest additionally prefixes every runtime image/video path with `import.meta.env.BASE_URL`, since Vite's `base` rewriting only covers build-time-processed references, not plain runtime string literals — this is what makes the site work correctly under a GitHub Pages **project subpath** (`/Decade-Hair/`) rather than only at a domain root.
3. `npm run build` produces a fully static `dist/` folder (HTML, hashed CSS/JS, fonts, and copied images/video).
4. The contents of `dist/` are copied to this repo's root (alongside `.nojekyll`, the favicon, and the original raw brand assets) and pushed to `main`.
5. GitHub Pages serves the site directly from `main` / `/ (root)` — no build step, no additional configuration required.

## Deployment (GitHub Pages)

**Settings → Pages → Source: Deploy from a branch → Branch: `main`, Folder: `/ (root)` → Save.**

Once enabled, the site is live at **https://kirans0615.github.io/Decade-Hair/**.

## Content status

Several pieces of copy on the site are realistic placeholders pending real studio information: the services menu/pricing, testimonial quotes, and the address/phone/hours/social links in the footer. See the development project's `ASSETS_AND_COPY_TODO.md` for the full list.
