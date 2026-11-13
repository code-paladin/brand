# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The shared brand package for Code Paladin web properties: `tokens.css` is a Tailwind v4 `@theme` block (colours, fonts, the 960px `page` container width) and `logos/` holds the logo assets. It is consumed as a git dependency (`github:code-paladin/brand`) by the corporate site and the blog. There is no build step, no tests and no JavaScript.

## Rules

- `tokens.css` must contain only `@theme` declarations. No selectors, no component styles, nothing site-specific; sites own their own layout CSS.
- Changing an existing token's value changes every consuming site. Adding a token is safe; renaming or removing one breaks consumers until they update, so treat it as a breaking change and bump the major version.
- Bump `version` in `package.json` and tag the commit (`v0.x.y`) for every change that consumers should pick up; sites pin to tags.
- Keep the README's token table in sync with `tokens.css`.
- Logos are the canonical files. If a site needs a variant, add it here, not in the site.
