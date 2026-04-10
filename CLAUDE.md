# Controlled Growth Theme — Instructions for Claude

This repo is a design system reference. When a user asks you to apply this theme to their project, follow these steps.

## How to Apply

1. **Read `controlled-growth.css`** — this is the single source of truth for all design tokens and component styles.
2. **Read `DESIGN.md`** — this has the full spec including canvas/JS color constants for data visualization.
3. **Adapt to the target project's stack:**
   - **Plain HTML/CSS**: Copy `controlled-growth.css` into the project. Add `class="cg-theme"` to `<body>`.
   - **React / Vue / Svelte**: Copy the `:root` custom properties block into the app's global CSS. Use the `cg-` class names on components, or map the variables to the framework's styling approach.
   - **Tailwind**: Translate the `:root` variables into `tailwind.config.js` `theme.extend` values. Map `--cg-cyan` → `colors.cg.cyan`, etc.
   - **CSS Modules / Styled Components**: Use the custom properties via `var(--cg-cyan)` etc. — they work anywhere once the `:root` block is loaded.

## Key Design Decisions

- **Dark terminal aesthetic**: near-black backgrounds (`#060611`), neon accents (cyan, green, pink, orange)
- **Monospace everywhere**: `'Courier New', 'Fira Code', monospace`
- **Hierarchy via opacity**, not color shifts — highlighted elements go to `opacity: 1`, de-emphasized drop to `0.15`
- **Borders at low opacity**: accent colors at `0.22` opacity for borders, `0.55` on hover
- **Glow effects**: `text-shadow` and `box-shadow` with accent colors for emphasis
- **All class names prefixed with `cg-`** to avoid conflicts

## Color Quick Reference

| Variable | Hex | Use for |
|----------|-----|---------|
| `--cg-cyan` | `#00ffc8` | Primary accent, links, highlights |
| `--cg-green` | `#00ff41` | Positive, success, support |
| `--cg-pink` | `#ff0066` | Negative, opposition, alerts |
| `--cg-orange` | `#ffa000` | Warnings, secondary actions |
| `--cg-purple` | `#bf5fff` | Special/unique identifiers |
| `--cg-bg-deep` | `#060611` | Page background |
| `--cg-bg` | `#0a0a1a` | Panel/container background |
| `--cg-text` | `#cdd6f4` | Body text |

## Do NOT

- Change the color values — they are carefully balanced for contrast on dark backgrounds
- Mix with light themes — this is dark-only by design
- Skip the monospace font — it's core to the aesthetic
