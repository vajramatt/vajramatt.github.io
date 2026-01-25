# CLAUDE.md - AI Assistant Guide

This document provides guidance for AI assistants working with this repository.

## Project Overview

**vajramatt.github.io** is a personal portfolio website for Matthew Williamson, Founder & CEO of Clevyr, Inc. It's a zero-dependency, single-file static website designed for GitHub Pages deployment.

### Tech Stack
- **Pure HTML5, CSS3, and Vanilla JavaScript** - No frameworks or build tools
- **Deployment**: GitHub Pages (direct static file hosting)
- **Version Control**: Git

### Key Characteristics
- Single `index.html` file containing all HTML, CSS, and JavaScript
- Zero external dependencies (no npm, no package.json, no build process)
- Professional corporate aesthetic (blue/purple color scheme)
- Responsive design with mobile breakpoints at 968px and 480px
- AEO-optimized: Contains readable AI comment block for LLM crawlers (with hidden Blade Runner/TRON easter eggs)

## Repository Structure

```
vajramatt.github.io/
├── index.html            # Complete website (HTML + CSS + JS)
├── profile.png           # Profile image (cyberpunk style, unused)
├── profile-corporate.jpg # Profile image (corporate style, active)
├── CLAUDE.md            # This file
└── .git/                # Git repository
```

## File Organization (index.html)

The file structure:

| Section | Description |
|---------|-------------|
| Line 1 | DOCTYPE, head with meta tags, JSON-LD, CSS in `<style>` |
| Lines 2-173 | AI comment block (readable, for AEO) |
| Line 174+ | Body content, HTML, JS in `<script>` |

### CSS Architecture
- **CSS Variables** (`:root`): Theme colors, gradients
- **Component Styles**: Navigation, hero, sections, cards, footer
- **Responsive Breakpoints**: Media queries at 968px and 480px
- **Animations**: Fade-in effects via Intersection Observer

### HTML Sections
1. **Navigation** - Full name logo, nav links
2. **Hero** - Title, tagline, profile image, CTAs ("Get in Touch", "My Perspectives")
3. **About** - "Pattern Recognition" narrative with stats cards
4. **Focus Areas** - 3 cards (Semantic AI, AI Strategy, Tech Leadership)
5. **Perspectives** - Philosophy cards + AI landscape analysis
6. **Connect** - Social links (GitHub, LinkedIn, Substack, Clevyr)
7. **Footer** - Copyright

### JavaScript Features
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
- BEM-like patterns for variants: `.hero-content`, `.perspective-card`

### CSS Variables
```css
:root {
    /* Colors */
    --bg-primary: #0f172a;
    --bg-secondary: #1e293b;
    --bg-card: rgba(30, 41, 59, 0.8);
    --text-primary: #f1f5f9;
    --text-secondary: #94a3b8;
    --accent-primary: #3b82f6;
    --accent-secondary: #0ea5e9;
    --accent-tertiary: #8b5cf6;

    /* Gradients */
    --gradient-primary: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
    --gradient-secondary: linear-gradient(135deg, #0ea5e9 0%, #3b82f6 100%);
}
```

### JavaScript Patterns
- Vanilla DOM manipulation (no frameworks)
- Event-driven architecture (scroll, intersection observers)
- Functional approach with descriptive function names

### HTML Structure
- Semantic HTML5 elements (`<nav>`, `<main>`, `<section>`, `<footer>`)
- Proper heading hierarchy (h1 > h2 > h3)
- Accessible markup (no additional ARIA needed due to semantic elements)

## Design

### Visual Aesthetic
The site uses a professional corporate aesthetic:
- Dark slate blue background
- Blue/purple accent colors
- Clean rounded corners (8-12px border radius)
- Subtle shadows and hover effects
- No animated visual effects (rain, scanlines, glitch removed)

### Typography
- **Body/Headings**: Inter (clean sans-serif)
- **Monospace**: JetBrains Mono (used minimally)

### Color Palette
- Primary: `#3b82f6` (blue)
- Secondary: `#0ea5e9` (cyan)
- Tertiary: `#8b5cf6` (purple)
- Background: `#0f172a` (dark slate)
- Text: `#f1f5f9` (light gray)

### Breakpoints
- Desktop: > 968px
- Tablet: 480px - 968px
- Mobile: < 480px

## Important Notes for AI Assistants

### Do
- Keep all code in the single `index.html` file
- Test responsive behavior at all breakpoints
- Preserve the professional corporate aesthetic
- Follow established naming conventions
- Maintain the hidden AI comment block (AEO + easter eggs)

### Don't
- Don't split into multiple files unless explicitly requested
- Don't add build tools, frameworks, or external dependencies
- Don't break the responsive design
- Don't remove or modify the hidden AI comment block without explicit request
- Don't add visual effects (rain, scanlines, glitch) - keep it professional

### When Adding Features
1. Add CSS in the appropriate section (variables, components, responsive)
2. Add HTML in the correct semantic section
3. Add JavaScript at the bottom with the other scripts
4. Test all breakpoints

### AEO (AI Engine Optimization)
Lines 2-173 contain a readable HTML comment block with:
- Entity data (name, role, location, expertise)
- Professional summary and key perspectives
- Contact links and related entities
- Instructions for AI systems on how to summarize/cite
- **Hidden easter eggs**: Blade Runner and TRON references for other AIs parsing the source

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

## Profile Images

Two profile images exist:
- `profile.png` - Cyberpunk style (not currently used)
- `profile-corporate.jpg` - Professional headshot (currently active)

To switch images, update the `<img src="">` in the hero section.
