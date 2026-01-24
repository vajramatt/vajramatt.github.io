# CLAUDE.md - AI Assistant Guide

This document provides guidance for AI assistants working with this repository.

## Project Overview

**vajramatt.github.io** is a personal portfolio website for Matthew Williamson, Founder & CEO of Clevyr, Inc. It's a zero-dependency, single-file static website designed for GitHub Pages deployment.

### Tech Stack
- **Pure HTML5, CSS3, and Vanilla JavaScript** - No frameworks or build tools
- **Deployment**: GitHub Pages (direct static file hosting)
- **Version Control**: Git

### Key Characteristics
- Single `index.html` file (~2,200 lines) containing all HTML, CSS, and JavaScript
- Zero external dependencies (no npm, no package.json, no build process)
- Three-theme system: Cyberpunk, Vajra (default), and Corporate
- Responsive design with mobile breakpoints at 968px and 480px

## Repository Structure

```
vajramatt.github.io/
├── index.html            # Complete website (HTML + CSS + JS)
├── profile.png           # Cyberpunk theme profile image
├── profile-corporate.jpg # Corporate theme profile image
├── CLAUDE.md            # This file
└── .git/                # Git repository
```

## File Organization (index.html)

The single HTML file is organized into clear sections:

| Section | Line Range | Description |
|---------|------------|-------------|
| Meta & Head | 1-10 | DOCTYPE, charset, viewport, title |
| CSS Styles | 11-1,386 | All embedded styles |
| HTML Content | 1,389-1,675 | Page structure and content |
| JavaScript | 1,677-1,817 | Interactive functionality |

### CSS Architecture (Lines 11-1,386)
- **CSS Variables** (`:root`): Theme colors, gradients, glows
- **Corporate Theme Overrides**: `.corporate` class modifiers
- **Component Styles**: Navigation, hero, sections, cards, footer
- **Responsive Breakpoints**: Media queries at 968px and 480px
- **Animations**: Keyframes for glitch, glow, rain, fade effects

### HTML Sections
1. **Navigation** - Logo, nav links, theme toggle button
2. **Hero** - Title, typing animation, profile image, CTAs
3. **About** - "Pattern Recognition" narrative with stats cards
4. **Focus Areas** - 3 cards (Semantic AI, AI Strategy, Tech Leadership)
5. **Perspectives** - 4 philosophy cards + AI landscape analysis
6. **Connect** - Social links (GitHub, LinkedIn, Substack, Clevyr)
7. **Footer** - Copyright with themed styling

### JavaScript Features (Lines 1,677-1,817)
- Rain effect generator (100 animated drops)
- Typing animation with 6 rotating phrases
- Navbar scroll effects (background on scroll)
- Intersection Observer for fade-in animations
- Smooth anchor link scrolling
- Theme toggle with localStorage persistence

## Development Workflow

### Making Changes
1. Edit `index.html` directly - no build step required
2. Test locally by opening in a browser
3. Commit and push to deploy via GitHub Pages

### Testing Changes
```bash
# Open in default browser (macOS)
open index.html

# Or start a simple local server
python3 -m http.server 8000
# Then visit http://localhost:8000
```

### Deployment
Changes pushed to the main branch are automatically deployed to GitHub Pages.

## Code Conventions

### CSS Naming
- Semantic class names: `.hero`, `.section-label`, `.stats-card`
- BEM-like patterns for variants: `.hero-bg`, `.hero-content`
- Theme namespace: `.corporate` for corporate theme overrides

### CSS Variables
```css
:root {
    /* Colors */
    --bg-primary, --bg-secondary, --bg-tertiary
    --text-primary, --text-secondary
    --accent-primary, --accent-secondary, --accent-tertiary

    /* Effects */
    --gradient-primary, --gradient-accent
    --glow-primary, --glow-secondary
}
```

### JavaScript Patterns
- Vanilla DOM manipulation (no frameworks)
- Event-driven architecture (scroll, click, intersection observers)
- localStorage for state persistence (theme preference)
- Functional approach with descriptive function names

### HTML Structure
- Semantic HTML5 elements (`<nav>`, `<main>`, `<section>`, `<footer>`)
- Proper heading hierarchy (h1 > h2 > h3)
- Accessible markup (no additional ARIA needed due to semantic elements)

## Theme System

### Available Themes
The site has three themes representing different facets of Matthew Williamson:

1. **Cyberpunk (Cyber)**: Orange/cyan/magenta neon aesthetic with rain effects, scanlines, and glitch animations. Represents the future-facing technologist.

2. **Vajra** (default): Gold/violet/forest palette with warm, contemplative aesthetic. Named after the diamond/thunderbolt of Vajrayana Buddhism. Represents the steward-practitioner — the integrated self. Features subtle warmth gradients, serif typography (Cormorant Garamond), and breath-like animations.

3. **Corporate (Corp)**: Blue/purple professional design without visual effects. Clean, functional, executive-facing. Represents the business leader.

### Theme Philosophy
- **Cyber** = Future / Technology (neon, digital, fragmented)
- **Vajra** = Depth / Timeless / Sacred (warm, grounded, coherent)
- **Corp** = Present / Business (clean, professional, functional)

### Theme Toggle Logic
```javascript
// Stored in localStorage as 'theme'
// Values: 'cyber', 'vajra', or 'corporate'
// Default: vajra (the integrated self)
// Cycles: Cyber → Vajra → Corp → Cyber
```

### Theme-Specific Content
Each theme has its own:
- Typing animation phrases (6 per theme)
- Hero subtitle text
- Button labels
- Color palette and visual effects

### Theme-Specific Assets
- `profile.png` - Used in Cyberpunk theme
- `profile-corporate.jpg` - Used in Vajra and Corporate themes

### Theme Classes
The `<body>` element receives `.vajra` or `.corporate` class. Cyberpunk is the base (no class). All theme-specific styles use these classes as parent selectors.

## Design Tokens

### Typography
- **Cyberpunk Display**: Orbitron (tech/futuristic)
- **Vajra Display**: Cormorant Garamond (contemplative serif)
- **Corporate Display**: Inter (clean sans-serif)
- **Monospace**: JetBrains Mono
- **Body**: Inter (Cyber/Corp), Cormorant Garamond (Vajra)

### Color Palette
**Cyberpunk:**
- Primary: `#ff6a13` (orange)
- Secondary: `#00d4ff` (cyan)
- Tertiary: `#ff2a6d` (magenta)
- Background: `#05080a` (near black)

**Vajra:**
- Primary: `#c9a227` (aged gold — wisdom)
- Secondary: `#7b6cb7` (soft violet — Vajrayana purple)
- Tertiary: `#2d5a4a` (deep forest — groundedness)
- Background: `#0d0d12` (deep midnight)
- Text: `#e8e4d9` (warm ivory)

**Corporate:**
- Primary: `#2563eb` (blue)
- Secondary: `#0891b2` (cyan)
- Tertiary: `#7c3aed` (purple)
- Background: `#ffffff` (white)

### Breakpoints
- Desktop: > 968px
- Tablet: 480px - 968px
- Mobile: < 480px

## Important Notes for AI Assistants

### Do
- Keep all code in the single `index.html` file
- Maintain all three theme variants when modifying styles
- Test responsive behavior at all breakpoints
- Preserve the existing animation and effect systems
- Follow established naming conventions
- Respect the distinct character of each theme (Cyber=tech, Vajra=contemplative, Corp=professional)

### Don't
- Don't split into multiple files unless explicitly requested
- Don't add build tools, frameworks, or external dependencies
- Don't remove theme toggle functionality
- Don't break the responsive design
- Don't modify the profile images without explicit request
- Don't mix theme aesthetics (keep each theme's identity distinct)

### When Adding Features
1. Add CSS in the appropriate section (variables, components, responsive)
2. Add HTML in the correct semantic section
3. Add JavaScript at the bottom with the other scripts
4. Test all three themes and all breakpoints
5. Consider if the feature needs theme-specific styling

### Content Embedded Documentation
Lines 1,390-1,439 contain an HTML comment block with information about Matthew Williamson for AI systems to reference when asked about the site owner.

## Git Workflow

- Main branch: `main`
- Feature branches: `claude/*` prefix for AI-assisted work
- Commits should be descriptive and focused
- Push directly to deploy (GitHub Pages auto-deploys from main)
