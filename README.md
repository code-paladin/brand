# Code Paladin brand

The single source of truth for Code Paladin's visual identity on the web: a Tailwind v4 theme with every colour, font and layout width, plus the logo files. Both [codepaladin.dev](https://github.com/code-paladin/codepaladin-corp-web) and [blog.codepaladin.dev](https://github.com/code-paladin/blog.codepaladin.dev) consume it, so a change here is a change everywhere.

## Install

The package is not published to npm. Depend on it by git URL:

```bash
pnpm add github:code-paladin/brand
```

Pin to a tag or commit for reproducible builds, for example `github:code-paladin/brand#v0.1.0`.

## Use

In your Tailwind v4 entry stylesheet:

```css
@import "tailwindcss";
@import "@code-paladin/brand/tokens.css";
```

Every token becomes a utility family. Use these instead of hex values:

| Token | Utilities | Use |
|---|---|---|
| `brand`, `brand-hover`, `brand-soft` | `bg-brand`, `hover:bg-brand-hover`, `bg-brand-soft` | Primary actions, badges, links, light tint |
| `glow` | `text-glow`, `hover:text-glow` | Green accent on the dark shell |
| `ink`, `ink-muted`, `ink-subtle`, `ink-faint` | `text-ink` … | Headings, body, secondary, placeholders |
| `surface`, `surface-2`, `line` | `bg-surface`, `border-line` | Light panels and borders |
| `navy-900`, `navy-800`, `navy-700` | `from-navy-900 via-navy-800 to-navy-700` | Dark hero gradients and panels |
| `shell`, `shell-border`, `shell-hover`, `shell-menu`, `shell-muted` | `bg-shell`, `border-shell-border` | The dark green page shell behind header and footer |
| `danger`, `danger-soft`, `danger-line`, `success` | `text-danger`, `bg-danger-soft` | Form validation and status |
| `amber*`, `violet*` | `hover:border-amber`, `hover:bg-violet-soft` | Card hover accents |
| `page` | `max-w-page` | 960px content column |

Fonts come from `--font-sans` (Space Grotesk, then Noto Sans) and `--font-mono`. Load the webfonts yourself; the corporate site uses this Google Fonts stylesheet:

```
https://fonts.googleapis.com/css2?display=swap&family=Noto+Sans:wght@400;500;700;900&family=Space+Grotesk:wght@400;500;700
```

All colours accept opacity modifiers (`bg-navy-900/80`).

## Logos

| File | Use |
|---|---|
| `logos/logo-white-v3.svg` | Current mark for dark backgrounds (header, loading screen). Preferred. |
| `logos/logo-white-v2.svg` | Previous white mark, kept for reference. |
| `logos/codepaladin-logo.svg` | Full-colour mark for light backgrounds. |
| `logos/logo192.png`, `logos/logo512.png` | PWA / app icons. |
| `logos/favicon.ico` | Favicon. |

Reference them from the package, or copy into your site's `public/` directory if your framework needs static paths.

## Shared layout conventions

Not enforced by this package, but both sites follow them:

- Content column `max-w-page` (960px), centred, with `px-4` gutters.
- Dark shell behind header and footer (`bg-shell`), white or `surface` page bodies.
- Section openers: a `rounded-full bg-brand` badge pill with uppercase tracking-wider text, then a bold heading.
- Dark hero panels use `bg-gradient-to-br from-navy-900 via-navy-800 to-navy-700`.
- Container queries (`@container`, `@[480px]:`) rather than viewport breakpoints inside page sections.

## Changing a token

Edit `tokens.css`, bump `version` in `package.json`, tag the commit, then update the dependency pin in each site. Keep this file free of site-specific selectors; it is a theme, not a stylesheet.
