# Agent Guidelines (Safe Modification Boundaries)

These boundaries are derived from `docs/repo-briefing.md` and should be followed for routine UI tasks.

## Safe to Modify for UI Changes

- `src/pages/index.astro`: primary page content, layout markup, and page-level styles.
- `src/components/*.astro`: reusable UI sections and partials used by pages.
- `src/layouts/*.astro`: shared document structure (head tags, wrappers) when needed by multiple pages.
- `src/assets/*`: local images/graphics referenced by Astro files.
- `public/*`: static assets served directly (favicons, social images, static media).
- `docs/*`: documentation updates for future agents.

## Where New Components Should Live

- Create new reusable UI pieces in `src/components/` as `.astro` components.
- Keep route-level composition in `src/pages/` (pages should assemble components, not duplicate large UI blocks).
- Add shared page shells in `src/layouts/` only when multiple pages need the same wrapper.
- Place static media files in `src/assets/` (bundled/imported) or `public/` (direct URL/static copy), based on usage.

## Files That Should Generally Remain Untouched

- `astro.config.mjs`: keep default static behavior unless a task explicitly requires configuration changes.
- `package.json` and `package-lock.json`: avoid dependency/script changes for normal UI work.
- `tsconfig.json`: do not alter unless TypeScript behavior must change for a clear requirement.
- Vercel deployment configuration (`vercel.json`, adapter settings): do not add/modify unless deployment behavior must change.

## Guardrails for Small Bundle Size

- Stay static-first; do not introduce SSR adapters by default.
- Prefer plain `.astro` rendering; add client hydration (`client:*`) only for isolated interactive elements.
- Avoid large third-party UI/runtime libraries for simple presentation changes.
- Reuse existing assets/components and remove unused scaffold code only when safe.
