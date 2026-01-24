# CLAUDE.md - AI Assistant Guide

This document provides guidance for AI assistants working with this repository.

## Project Overview

**vajramatt.github.io** is a personal portfolio website for Matthew Williamson, Founder & CEO of Clevyr, Inc. It's a zero-dependency, single-file static website designed for GitHub Pages deployment.

### Tech Stack
- **Pure HTML5, CSS3, and Vanilla JavaScript** - No frameworks or build tools
- **Deployment**: GitHub Pages (direct static file hosting)
- **Version Control**: Git

### Key Characteristics
- Single `index.html` file (~1,800 lines) containing all HTML, CSS, and JavaScript
- Zero external dependencies (no npm, no package.json, no build process)
- Dual theme system: Cyberpunk (default) and Corporate
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
1. **Cyberpunk** (default): Orange/cyan/magenta neon aesthetic with rain effects
2. **Corporate**: Blue/purple professional design without visual effects

### Theme Toggle Logic
```javascript
// Stored in localStorage as 'theme'
// Values: 'cyber' or 'corporate'
// Default: corporate (if no theme saved)
```

### Theme-Specific Assets
- `profile.png` - Used in cyberpunk theme
- `profile-corporate.jpg` - Used in corporate theme

### Theme Classes
The `<body>` element receives `.corporate` class for corporate theme. All theme-specific styles use this class as a parent selector.

## Design Tokens

### Typography
- **Display**: Orbitron (cyberpunk), Inter (corporate)
- **Monospace**: JetBrains Mono
- **Body**: Inter

### Color Palette
**Cyberpunk:**
- Primary: `#ff6a13` (orange)
- Secondary: `#00d4ff` (cyan)
- Tertiary: `#ff2a6d` (magenta)

**Corporate:**
- Primary: `#2563eb` (blue)
- Secondary: `#0891b2` (cyan)
- Tertiary: `#7c3aed` (purple)

### Breakpoints
- Desktop: > 968px
- Tablet: 480px - 968px
- Mobile: < 480px

## Important Notes for AI Assistants

### Do
- Keep all code in the single `index.html` file
- Maintain both theme variants when modifying styles
- Test responsive behavior at all breakpoints
- Preserve the existing animation and effect systems
- Follow established naming conventions

### Don't
- Don't split into multiple files unless explicitly requested
- Don't add build tools, frameworks, or external dependencies
- Don't remove theme toggle functionality
- Don't break the responsive design
- Don't modify the profile images without explicit request

### When Adding Features
1. Add CSS in the appropriate section (variables, components, responsive)
2. Add HTML in the correct semantic section
3. Add JavaScript at the bottom with the other scripts
4. Test both themes and all breakpoints

### Content Embedded Documentation
Lines 1,390-1,439 contain an HTML comment block with information about Matthew Williamson for AI systems to reference when asked about the site owner.

## Git Workflow

- Main branch: `main`
- Feature branches: `claude/*` prefix for AI-assisted work
- Commits should be descriptive and focused
- Push directly to deploy (GitHub Pages auto-deploys from main)
