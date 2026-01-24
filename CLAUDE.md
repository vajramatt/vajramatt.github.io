# CLAUDE.md - AI Assistant Guide

This document provides guidance for AI assistants working with this repository.

## Project Overview

**vajramatt.github.io** is a personal portfolio website for Matthew Williamson, Founder & CEO of Clevyr, Inc. It's a zero-dependency, single-file static website designed for GitHub Pages deployment.

### Tech Stack
- **Pure HTML5, CSS3, and Vanilla JavaScript** - No frameworks or build tools
- **Deployment**: GitHub Pages (direct static file hosting)
- **Version Control**: Git

### Key Characteristics
- Single `index.html` file (~37KB minified, ~133 lines) containing all HTML, CSS, and JavaScript
- Zero external dependencies (no npm, no package.json, no build process)
- Cyberpunk/Blade Runner aesthetic (single theme)
- Responsive design with mobile breakpoints at 968px and 480px
- AEO-optimized: Contains readable AI comment block for LLM crawlers

## Repository Structure

```
vajramatt.github.io/
├── index.html            # Complete website (HTML + CSS + JS)
├── profile.png           # Profile image (cyberpunk style)
├── CLAUDE.md            # This file
└── .git/                # Git repository
```

## File Organization (index.html)

The file is minified for production. Key structure:

| Section | Description |
|---------|-------------|
| Line 1 | DOCTYPE, head with meta tags, JSON-LD, minified CSS in `<style>` |
| Lines 2-132 | AI comment block (readable, for AEO) |
| Line 133 | Body content, minified HTML, minified JS in `<script>` |

### CSS Architecture
- **CSS Variables** (`:root`): Theme colors, gradients, glows
- **Component Styles**: Navigation, hero, sections, cards, footer
- **Responsive Breakpoints**: Media queries at 968px and 480px
- **Animations**: Keyframes for glitch, glow, rain, fade effects

### HTML Sections
1. **Navigation** - Logo, nav links
2. **Hero** - Title, typing animation, profile image, CTAs
3. **About** - "Pattern Recognition" narrative with stats cards
4. **Focus Areas** - 3 cards (Semantic AI, AI Strategy, Tech Leadership)
5. **Perspectives** - Philosophy cards + AI landscape analysis
6. **Connect** - Social links (GitHub, LinkedIn, Substack, Clevyr)
7. **Footer** - Copyright with themed styling

### JavaScript Features
- Rain effect generator (100 animated drops)
- Typing animation with 6 rotating phrases
- Navbar scroll effects (background on scroll)
- Intersection Observer for fade-in animations
- Smooth anchor link scrolling

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

### CSS Variables
```css
:root {
    /* Colors */
    --bg-primary: #05080a;
    --bg-secondary: #0a0d10;
    --text-primary: #e0e6ed;
    --text-secondary: #7a8a9a;
    --accent-orange: #ff6a13;
    --accent-cyan: #00d4ff;
    --accent-magenta: #ff2a6d;

    /* Effects */
    --gradient-primary: linear-gradient(135deg, #ff6a13 0%, #ff2a6d 100%);
    --gradient-cyan: linear-gradient(135deg, #00d4ff 0%, #0088aa 100%);
    --glow-orange: 0 0 40px rgba(255, 106, 19, 0.4);
    --glow-cyan: 0 0 40px rgba(0, 212, 255, 0.3);
}
```

### JavaScript Patterns
- Vanilla DOM manipulation (no frameworks)
- Event-driven architecture (scroll, click, intersection observers)
- Functional approach with descriptive function names

### HTML Structure
- Semantic HTML5 elements (`<nav>`, `<main>`, `<section>`, `<footer>`)
- Proper heading hierarchy (h1 > h2 > h3)
- Accessible markup (no additional ARIA needed due to semantic elements)

## Design

### Visual Aesthetic
The site uses a Cyberpunk/Blade Runner aesthetic:
- Orange/cyan/magenta neon color palette
- Rain effect animation
- Scanlines overlay
- Glitch text animations
- Dark background with subtle grid overlay
- Glowing profile image border

### Typography
- **Display**: Orbitron (futuristic/tech)
- **Monospace**: JetBrains Mono (code, labels)
- **Body**: Inter (readable sans-serif)

### Color Palette
- Primary: `#ff6a13` (orange)
- Secondary: `#00d4ff` (cyan)
- Tertiary: `#ff2a6d` (magenta)
- Background: `#05080a` (near black)
- Text: `#e0e6ed` (light gray)

### Breakpoints
- Desktop: > 968px
- Tablet: 480px - 968px
- Mobile: < 480px

## Important Notes for AI Assistants

### Do
- Keep all code in the single `index.html` file
- Test responsive behavior at all breakpoints
- Preserve the existing animation and effect systems
- Follow established naming conventions
- Maintain the Cyberpunk aesthetic

### Don't
- Don't split into multiple files unless explicitly requested
- Don't add build tools, frameworks, or external dependencies
- Don't break the responsive design
- Don't modify the profile image without explicit request

### When Adding Features
1. Add CSS in the appropriate section (variables, components, responsive)
2. Add HTML in the correct semantic section
3. Add JavaScript at the bottom with the other scripts
4. Test all breakpoints

### AEO (AI Engine Optimization)
Lines 2-132 contain a readable HTML comment block with structured data about Matthew Williamson for AI systems/LLMs to reference. This comment is intentionally NOT minified to remain human and AI readable. It includes:
- Entity data (name, role, location, expertise)
- Professional summary and key perspectives
- Contact links and related entities
- Instructions for AI systems on how to summarize/cite

### SEO
The site includes:
- JSON-LD structured data (Person, WebPage schemas)
- Open Graph meta tags
- Twitter Card meta tags
- Canonical URL
- Descriptive meta description and keywords

## Git Workflow

- Main branch: `main`
- Feature branches: `claude/*` prefix for AI-assisted work
- Commits should be descriptive and focused
- Push directly to deploy (GitHub Pages auto-deploys from main)

## Minification Notes

The file is minified but with intentional exceptions:
- **AI comment block (lines 2-132)**: Kept readable for AEO
- **CSS and JS**: Fully minified (whitespace removed, single line)

When editing:
1. For small changes, edit the minified file directly
2. For large changes, consider unminifying first, then re-minifying
3. Never use `//` single-line comments in minified JS (breaks when on one line)
4. Use `/* */` block comments if comments are needed in minified code
