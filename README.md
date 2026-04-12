# Controlled Growth Theme

Light, organic design system with muted green accents and frosted glass panels. Extracted from the [Yberg Counsel](https://github.com/tcmberg/yberg_counsel) WebUI. One CSS file, drop it into any project.

## Usage

```html
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;700&family=IBM+Plex+Sans:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<link rel="stylesheet" href="controlled-growth.css">
<body class="cg-theme">
  <!-- your app -->
</body>
```

Or copy the CSS custom properties from `:root` into your own stylesheet.

## Files

| File | Description |
|------|-------------|
| `controlled-growth.css` | Full CSS — custom properties + component classes |
| `DESIGN.md` | Complete design reference (colors, typography, patterns, canvas config) |
| `example.html` | Visual preview of all components |

## Preview

Open `example.html` in a browser to see all components.

## What's Included

- CSS custom properties (design tokens) for colors, spacing, typography, shadows
- Three font families: Fraunces (headings), IBM Plex Sans (body), JetBrains Mono (UI/code)
- Frosted glass panel effect with backdrop blur
- Subtle fractal noise background texture
- Base styles, typography, text color utilities
- Panels, cards, message cards, observer cards, summary cards
- Buttons (4 color variants, active state, link-style)
- Badges (support/oppose/unsure) and tags
- Topbar, pipeline progress, layout mode switcher
- Tooltips, legends, form inputs
- Detail sections for side panels
- HUD corner bracket decorations
- Mention tag styling
- Summary grid for statistics
- Pulse and dot animations
- Custom scrollbar styling
- Canvas/JS color constants for data visualization (in DESIGN.md)
