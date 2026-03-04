# Repo Briefing (TruChrome)

## Framework and Rendering Mode

- Framework: Astro v5 (`type: module`).
- Rendering mode: static site generation (`astro build` outputs static files to `dist/`).

## Folder Structure

- `src/pages/`: route entrypoints (`index.astro` is the live page).
- `public/`: static files copied directly into build output (favicons).
- `src/layouts/`, `src/components/`, `src/assets/`: starter scaffold directories; mostly unused right now.
- `astro.config.mjs`: minimal default Astro config.
- `dist/`: generated build output (gitignored).

## Build and Dev Commands

- `npm run dev`: start Astro dev server.
- `npm run build`: create production static build in `dist/`.
- `npm run preview`: preview the production build locally.
- `npm run astro`: Astro CLI passthrough.

## Deployment Behavior on Vercel

- No `vercel.json` and no Astro Vercel adapter are configured.
- Vercel auto-detects Astro, runs `npm run build`, and serves `dist/` as a static deployment.
- Current deployment is pure static output (`index.html` + public assets), with no serverless runtime required.

## Constraints to Keep Bundle Size Small

- Keep the project static-first; avoid adding SSR adapters unless truly needed.
- Prefer `.astro` server-rendered markup over client-hydrated islands.
- If interactivity is required, hydrate only small isolated components (`client:*`).
- Keep dependencies minimal; avoid heavy UI/framework libraries for simple pages.
- Optimize assets: use SVG where practical, compress images, and keep fonts minimal (or use system fonts).
- Remove unused scaffold files/components when safe to reduce maintenance and accidental imports.
