# Controlled Growth Design System

Light, organic aesthetic with muted green accents and frosted glass panels. Extracted from the Yberg Counsel WebUI. Three font families for visual hierarchy. Subtle borders, backdrop blur, and gentle hover effects.

## Color Palette

### Brand Accents
| Token | Hex | Usage |
|-------|-----|-------|
| `--cg-green` | `#27A85A` | Primary accent, links, highlights, support |
| `--cg-red` | `#E05C5C` | Opposition/negative, alerts |
| `--cg-yellow` | `#B07D10` | Uncertainty, warnings |
| `--cg-purple` | `#c084fc` | Tension edges, special states |

### Backgrounds
| Token | Value | Usage |
|-------|-------|-------|
| `--cg-bg` | `#F4F6F2` | Page background (cream with fractal noise) |
| `--cg-surface` | `rgba(255,255,255,0.65)` | Panels, frosted glass containers |
| `--cg-card` | `rgba(244,246,242,0.7)` | Cards, secondary containers |

### Text (dark to light)
| Token | Hex | Usage |
|-------|-----|-------|
| `--cg-text` | `#1F2A23` | Primary readable text |
| `--cg-text-muted` | `#3A3F3C` | Secondary text |
| `--cg-text-dim` | `#6E8B6B` | Tertiary/de-emphasized text |

### Accent Variants
| Token | Value | Usage |
|-------|-------|-------|
| `--cg-accent` | `#27A85A` | Alias for primary green |
| `--cg-accent-dim` | `rgba(39,168,90,0.4)` | Hover borders, glow shadows |
| `--cg-accent-bg` | `rgba(39,168,90,0.08)` | Active button fills, subtle highlights |

## Typography

Three font families create visual hierarchy:

- **Heading**: `'Fraunces', Georgia, serif` — weight 400/700
- **Body**: `'IBM Plex Sans', system-ui, sans-serif` — weight 400/500/600
- **Mono**: `'JetBrains Mono', 'SF Mono', Consolas, monospace` — weight 400/500

**Google Fonts import:**
```html
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;700&family=IBM+Plex+Sans:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Size Scale
| Element | Size | Weight | Family | Details |
|---------|------|--------|--------|---------|
| Title | 13px | 700 | Mono | uppercase, `letter-spacing: 3px` |
| Section label | 11px | 600 | Mono | uppercase, `letter-spacing: 2px` |
| Body | 14px | 400 | Body | `line-height: 1.75` |
| Pipeline step | 11px | 500 | Mono | uppercase, `letter-spacing: 0.8px` |
| Button | 12px | 500 | Body | |
| Badge | 12px | 600 | Body | |
| Small meta | 10-11px | 500 | Mono | uppercase, `letter-spacing: 1px` |
| Detail name | 18px | 700 | Body | |
| Summary value | 20px | 700 | Mono | |

## Borders & Outlines

Borders are nearly invisible — accent color at very low opacity:
- Standard: `1px solid rgba(31, 42, 35, 0.08)` (the `--cg-border` token)
- Hover: `rgba(31, 42, 35, 0.14)` — barely brightens
- Summary card: `1px solid rgba(39, 168, 90, 0.2)` — green tint
- Left accent: `3px solid` on message/observer cards
- HUD corners: `2px solid rgba(31, 42, 35, 0.12)` top, `0.08` bottom

### Vote badge borders
- Support: `1px solid rgba(39, 168, 90, 0.22)`
- Oppose: `1px solid rgba(224, 92, 92, 0.22)`
- Unsure: `1px solid rgba(176, 125, 16, 0.22)`

## Frosted Glass Effect

The signature visual — semi-transparent backgrounds with backdrop blur:
```css
background: rgba(255, 255, 255, 0.65);
backdrop-filter: blur(12px);
-webkit-backdrop-filter: blur(12px);
```
Used on panels, topbar (`blur(8px)`), legends, tooltips.

## Background Texture

Subtle fractal noise overlay at 3% opacity:
```css
background-image: url("data:image/svg+xml,...feTurbulence type='fractalNoise' baseFrequency='0.9'...");
background-size: 200px 200px;
```

## Shadows

Minimal, organic shadows (no glows):
- Small: `0 1px 3px rgba(31, 42, 35, 0.06)`
- Medium: `0 4px 12px rgba(31, 42, 35, 0.08)`
- Active dot: `0 0 8px rgba(39, 168, 90, 0.4)`

## Component Patterns

### Message Cards
- Background: `var(--cg-surface)` (frosted white)
- Border: `1px solid var(--cg-border)`
- Left accent border: `3px solid [botColor]`
- Border-radius: `10px`
- Padding: `16px 18px`
- Top line: `linear-gradient(90deg, transparent, rgba(39,168,90,0.08), transparent)`
- Hover: `translateY(-1px)`, border brightens

### Buttons
- Background: `var(--cg-card)`, colored text
- Border: `1px solid var(--cg-border)`
- Hover: background becomes border color, text becomes accent
- Toggle buttons: 28x28px square, icon-only
- Layout mode buttons: grouped in pill container

### Badges (vote/status)
- Pill-shaped (`border-radius: 20px`)
- Tinted background at 12% opacity
- Colored text matching the semantic meaning
- Thin border at 22% opacity of the same color

### Topbar
- Height: 48px
- Frosted background: `rgba(244,246,242,0.88)` + `blur(8px)`
- Title in mono, topic truncated, stats on right

### Pipeline
- Height: 36px
- Steps with 8px dots, arrows between
- Active: green with pulsing dot shadow
- Done: solid green

### HUD Corner Brackets
- 28x28px corners
- Top corners: `rgba(31,42,35,0.12)` — subtle
- Bottom corners: `rgba(31,42,35,0.08)` — even subtler
- All using the dark text color, not accent colors

## Canvas / Visualization Colors

For JS canvas rendering (graphs, data viz):

```javascript
const CG_CANVAS = {
  // Entity node colors by type
  component: '#6E8B6B',  // muted sage
  person:    '#EF4444',  // red
  concept:   '#22C55E',  // bright green
  org:       '#F59E0B',  // amber

  // Edge colors
  reply:     '#27A85A',  // green — bot-to-bot connections
  entity:    '#6E8B6B',  // sage — entity relationships
  tension:   '#c084fc',  // purple — disagreement/conflict

  // Text on canvas
  label:     '#1F2A23',  // dark text
  labelFont: '500 11px IBM Plex Sans, sans-serif',

  // Background
  bg:        '#F4F6F2',
  glow:      'radial-gradient(ellipse, rgba(39,168,90,0.03), transparent 70%)',

  // Branch tree (decorative background)
  branch:    'rgba(31,42,35,0.12-0.18)',  // very subtle dark strokes

  // Selection highlight
  selected:  '#27A85A',

  // Node shapes
  // Entities: circles (radius 6-18px based on connections)
  // Bots: squares (radius 4-6px)
};
```

## Animations

- **Pulse**: opacity 0.2 → 0.8 → 0.2 over 1.4s (typing indicators)
- **Pulse dot**: opacity+scale 1.0/1.0 → 0.4/0.85 over 2.4s (pipeline dots)
- **Standard transition**: `all 0.15s ease`
- **Panel transition**: `all 0.4s cubic-bezier(0.4, 0, 0.2, 1)`
- **Hover lift**: `transform: translateY(-1px)` at 0.15s

## Quick Start

```html
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;700&family=IBM+Plex+Sans:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<link rel="stylesheet" href="controlled-growth.css">
<body class="cg-theme">
  <div class="cg-topbar">
    <span class="cg-title">λ Project</span>
    <span class="cg-topbar-topic">Description here</span>
  </div>
  <div class="cg-panel cg-panel-frosted cg-hud-corners">
    <span class="cg-section-label">Status</span>
    <span class="cg-badge cg-badge--support">Active</span>
  </div>
  <button class="cg-btn">Action</button>
  <input class="cg-input" placeholder="Type here...">
</body>
```
