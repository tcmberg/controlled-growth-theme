# Controlled Growth Theme — Instructions for Claude

This repo is a design system reference extracted from the Yberg Counsel WebUI. When a user asks you to apply this theme to their project, follow these steps.

## How to Apply

1. **Read `controlled-growth.css`** — this is the single source of truth for all design tokens and component styles.
2. **Read `DESIGN.md`** — this has the full spec including canvas/JS color constants for data visualization.
3. **Adapt to the target project's stack:**
   - **Plain HTML/CSS**: Copy `controlled-growth.css` into the project. Add `class="cg-theme"` to `<body>`. Include the Google Fonts link for Fraunces, IBM Plex Sans, and JetBrains Mono.
   - **React / Vue / Svelte**: Copy the `:root` custom properties block into the app's global CSS. Use the `cg-` class names on components, or map the variables to the framework's styling approach.
   - **Tailwind**: Translate the `:root` variables into `tailwind.config.js` `theme.extend` values. Map `--cg-green` → `colors.cg.green`, etc.
   - **CSS Modules / Styled Components**: Use the custom properties via `var(--cg-green)` etc. — they work anywhere once the `:root` block is loaded.

## Key Design Decisions

- **Light, organic aesthetic**: cream background (`#F4F6F2`) with fractal noise texture, frosted glass panels
- **Three font families**: Fraunces (serif headings), IBM Plex Sans (body), JetBrains Mono (UI labels/code)
- **Muted green accent**: `#27A85A` — not neon, not pastel
- **Frosted glass panels**: `rgba(255,255,255,0.65)` with `backdrop-filter: blur(12px)`
- **Nearly invisible borders**: `rgba(31, 42, 35, 0.08)` — felt, not seen
- **Hover via lift**: `translateY(-1px)` rather than color shifts
- **Badges use tinted backgrounds** at 12% opacity with matching 22% opacity borders
- **All class names prefixed with `cg-`** to avoid conflicts

## Color Quick Reference

| Variable | Value | Use for |
|----------|-------|---------|
| `--cg-green` | `#27A85A` | Primary accent, links, highlights, support |
| `--cg-red` | `#E05C5C` | Opposition, negative, alerts |
| `--cg-yellow` | `#B07D10` | Uncertainty, warnings |
| `--cg-purple` | `#c084fc` | Tension, special states |
| `--cg-bg` | `#F4F6F2` | Page background |
| `--cg-surface` | `rgba(255,255,255,0.65)` | Panel/container background |
| `--cg-card` | `rgba(244,246,242,0.7)` | Card background |
| `--cg-text` | `#1F2A23` | Body text |
| `--cg-text-muted` | `#3A3F3C` | Secondary text |
| `--cg-text-dim` | `#6E8B6B` | Tertiary/de-emphasized text |

## Do NOT

- Change the color values — they are carefully balanced for contrast on light backgrounds
- Mix with dark themes — this is light-only by design
- Skip the Google Fonts import — the three font families are core to the aesthetic
- Use heavy drop shadows or glows — the design relies on subtlety (frosted glass, nearly invisible borders)
