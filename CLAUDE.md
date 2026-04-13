# Controlled Growth Theme — Instructions for Claude

This repo is a design system reference extracted from the Yberg Counsel WebUI. It ships in two variants: **light** (default) and **dark mud**. When a user asks you to apply this theme to their project, follow these steps.

## How to Apply

1. **Read `controlled-growth.css`** — this is the single source of truth for all design tokens and component styles.
2. **Read `controlled-growth-dark.css`** — the dark mud variant that overrides tokens with warm brown/earth tones.
3. **Read `DESIGN.md`** — this has the full spec including canvas/JS color constants for data visualization.
4. **Adapt to the target project's stack:**
   - **Plain HTML/CSS**: Copy `controlled-growth.css` (and optionally `controlled-growth-dark.css`) into the project. Add `class="cg-theme"` to `<body>` for light, or `class="cg-theme cg-dark"` for dark mud. Include the Google Fonts link for Fraunces, IBM Plex Sans, and JetBrains Mono.
   - **React / Vue / Svelte**: Copy the `:root` custom properties block into the app's global CSS. Use the `cg-` class names on components. Toggle dark mode by adding/removing the `cg-dark` class.
   - **Tailwind**: Translate the `:root` variables into `tailwind.config.js` `theme.extend` values. Map `--cg-green` → `colors.cg.green`, etc.
   - **CSS Modules / Styled Components**: Use the custom properties via `var(--cg-green)` etc. — they work anywhere once the `:root` block is loaded.

## Key Design Decisions

### Light variant
- **Light, organic aesthetic**: cream background (`#F4F6F2`) with fractal noise texture, frosted glass panels
- **Muted green accent**: `#27A85A` — not neon, not pastel
- **Frosted glass panels**: `rgba(255,255,255,0.65)` with `backdrop-filter: blur(12px)`
- **Nearly invisible borders**: `rgba(31, 42, 35, 0.08)` — felt, not seen

### Dark mud variant
- **Warm earth aesthetic**: rich brown background (`#28231E`) — never black
- **Clay accent**: `#B08860` — warm, earthy, easy on the eyes
- **Dark frosted glass panels**: `rgba(55, 47, 38, 0.65)` with backdrop blur
- **Cream text**: `#E2D9CE` — parchment tone, not harsh white
- **Slightly stronger shadows**: to register on dark surfaces

### Shared
- **Three font families**: Fraunces (serif headings), IBM Plex Sans (body), JetBrains Mono (UI labels/code)
- **Hover via lift**: `translateY(-1px)` rather than color shifts
- **Badges use tinted backgrounds** at ~12% opacity with matching ~22% opacity borders
- **All class names prefixed with `cg-`** to avoid conflicts

## Color Quick Reference

### Light
| Variable | Value | Use for |
|----------|-------|---------|
| `--cg-accent` | `#27A85A` | Primary accent (green) |
| `--cg-bg` | `#F4F6F2` | Page background |
| `--cg-surface` | `rgba(255,255,255,0.65)` | Panel background |
| `--cg-text` | `#1F2A23` | Body text |

### Dark Mud
| Variable | Value | Use for |
|----------|-------|---------|
| `--cg-accent` | `#B08860` | Primary accent (clay) |
| `--cg-bg` | `#28231E` | Page background |
| `--cg-surface` | `rgba(55,47,38,0.65)` | Panel background |
| `--cg-text` | `#E2D9CE` | Body text |

## Do NOT

- Change the color values — they are carefully balanced for contrast within each variant
- Skip the Google Fonts import — the three font families are core to the aesthetic
- Use heavy drop shadows or glows — the design relies on subtlety (frosted glass, nearly invisible borders)
- Mix light and dark token values — use one variant or the other
