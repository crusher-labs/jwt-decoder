# AGENTS.md - JWT Decoder

Single-purpose static tool: Decode and inspect JWT tokens without sending them to a server. Part of the crusher-labs **static tools line** (frozen). Hosted on GitHub Pages at https://crusher-labs.github.io/jwt-decoder/

Workspace rules: `x:\crusher-labs\AGENTS.md`. Global rules: `~/.claude/CLAUDE.md`.

## What it is

- One `index.html`, no build step, no backend, fully client-side.
- Consumes `crusher-ui-kit` via the jsDelivr CDN (the workspace static contract).

## Static contract (must hold)

- `<html>` carries `data-default-theme="minimal" data-theme-lock="minimal" data-default-mode="dark" data-default-brand="#0ea5e9"`; `<body class="crusher-tool-page">`; one fixed `<crusher-style-switcher>`. No Tailwind CDN, no Font Awesome.
- Validated by `tools-hub/scripts/check-static.mjs` (run `npm run check:static` from `repos/tools-hub`).

## Status: FROZEN

The static tools line is frozen at 30 (strategy: `x:\crusher-labs\docs\context\strategy-analysis.md`). Don't add features or tools without a strategy revisit.

## What NOT to do

- Don't commit to `main` directly (`dev` -> manual QA -> fast-forward `main`). No `Co-Authored-By` / AI-attribution trailers.
- Don't edit `crusher-ui-kit`; request changes via the workspace `private/framework-feedback.md`.
- Don't add Tailwind CDN / Font Awesome; use framework primitives + inline SVGs.
