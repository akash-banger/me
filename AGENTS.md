## What this is

Akash Banger's public personal website (akashbanger.vercel.app), an Astro static site, public from its first commit. V1 is deliberately Home-only: Projects, Writing, and Post pages, the notify-me backend, and a custom domain are deferred until Akash says go.

## Commands

See README.md. There are no tests or linters; verification for a change is a local build plus the screenshot review in the deploy workflow below.

## Deploy workflow (non-negotiable)

- Iterate locally first: verify every change on this machine (local build; for visual work, a screenshot or dev-server review Akash approves) before pushing anything. The Vercel preview confirms an already-approved change; it is not the iteration loop.
- Every change rides a feature branch and a PR. `main` is protected by a GitHub ruleset with no bypass actors; no token can push it directly.
- Vercel builds each PR into a preview deployment and its `Vercel` check must pass. Production ships only by merging to `main`; deploy by merge, never by CLI.
- Only Akash merges: in the GitHub UI, or by saying so explicitly, after which `gh pr merge` is fine. Squash merges only; branches auto-delete.

## Architecture

- `src/styles/tokens.css` is the design source of truth: every font, size, color, radius, spacing, and motion value. Dark theme is default; light activates via `data-theme="light"` on `<html>`. Change design decisions here, not inline.
- `src/styles/system.css` holds the reusable components. Both files came from a design handoff and stay close to verbatim.
- `src/pages/index.astro` is the whole site: markup, page-specific overrides, the pre-paint theme script, and the theme toggle.
- `public/` holds self-hosted fonts (Bricolage Grotesque display, Inter body, JetBrains Mono strictly for meta), pre-optimized images, OG card, favicon. The site makes no external requests.

## Content rules

- Punctuate public text with periods, commas, colons, or parentheses; the em dash is banned everywhere public, including commit messages and PR text.
- Site content is limited to what Akash has explicitly approved. Biographical details, employers, clients, or engagements beyond the existing copy need his sign-off first.
- Every claim on the site must be true the day it ships: only real projects, real stats, essays that exist.
- License is MIT for code only; photos, images, and prose are all rights reserved (see LICENSE).
