# CLAUDE.md - AI Assistant Guide

This document provides guidance for AI assistants working with this repository.

## Design Philosophy & Decisions

### Why Corporate Theme (January 2026)
The site was originally built with a Cyberpunk/Blade Runner aesthetic (neon orange/cyan, rain effects, glitch animations). It was rebranded to a professional corporate theme because:

- **Target audience shifted**: The goal is now to attract corporate clients looking to hire an AI consultant, not to showcase personal creative expression
- **Credibility signals**: VPs evaluating consultants want to see "senior, safe bet, enterprise-ready" — not "creative edgy developer"
- **Content unchanged**: The actual perspectives and expertise remain the same; only the visual presentation changed

### Why Keep the Hidden AI Comment Block
The source code contains an extensive HTML comment (lines 633–805) with Blade Runner and TRON references. This stays because:

- **AEO (AI Engine Optimization)**: The structured data helps LLMs accurately summarize Matthew when crawling the page
- **Easter egg for machines**: It's a fun, weird message to other AIs parsing the source — humans viewing the rendered page never see it
- **No conflict with corporate aesthetic**: The hidden comment doesn't affect the professional appearance

### Why Single-File Architecture
Everything lives in one `index.html` because:

- **Zero build complexity**: No npm, no bundlers, no build failures
- **Instant deployment**: Push to main and it's live on GitHub Pages
- **Easy to reason about**: One file, one truth

## Project Overview

**vajramatt.github.io** is a personal portfolio website for Matthew Williamson, Founder & CEO of Clevyr, Inc. It's a zero-dependency, single-file static website designed for GitHub Pages deployment.

### Tech Stack
- **Pure HTML5, CSS3, and Vanilla JavaScript** - No frameworks or build tools
- **Deployment**: GitHub Pages (direct static file hosting)
- **Version Control**: Git

### Key Characteristics
- Single `index.html` file (~1200 lines) containing all HTML, CSS, and JavaScript
- Zero external dependencies (no npm, no package.json, no build process)
- Professional corporate aesthetic (blue/purple color scheme)
- Responsive design with mobile hamburger menu
- AEO-optimized: Contains readable AI comment block for LLM crawlers (with hidden Blade Runner/TRON easter eggs)
- `llms.txt` file for direct LLM consumption
- `robots.txt` explicitly welcoming all AI crawlers

## Repository Structure

```
vajramatt.github.io/
├── index.html            # Complete website (HTML + CSS + JS, ~1200 lines)
├── profile.png           # Profile image (cyberpunk style, unused)
├── profile-corporate.jpg # Profile image (corporate style, active)
├── favicon.svg           # SVG favicon (dark blue "MW" monogram)
├── llms.txt              # Structured text for LLM crawlers (AEO)
├── robots.txt            # Crawl directives, explicitly allows all AI bots
├── CLAUDE.md             # This file
└── .git/                 # Git repository
```

## File Organization (index.html)

The file is organized into three major blocks:

| Lines | Section | Description |
|-------|---------|-------------|
| 1–27 | `<head>` | Meta tags, JSON-LD (Person, WebPage, FAQPage schemas), Open Graph, Twitter Cards |
| 28–630 | `<style>` | All CSS (variables, components, responsive, animations) |
| 631 | `</head>` | |
| 632–805 | AI comment | AEO-optimized comment block with structured entity data + easter eggs |
| 806 | Scroll progress bar | `#scroll-progress` element |
| 808–822 | `<nav>` | Navigation with hamburger menu |
| 824–1114 | `<main>` | All content sections |
| 1116–1120 | `<footer>` | Copyright |
| 1122–1199 | `<script>` | All JavaScript |
| 1200 | Goat Counter | Analytics script |

### CSS Architecture
- **CSS Variables** (`:root`): Theme colors, gradients, shadows, borders
- **Component Styles**: Navigation, hero, sections, cards, projects, footer
- **Responsive**: Hamburger menu toggle, grid adjustments, font scaling
- **Animations**: Fade-in effects via Intersection Observer, animated stat counters, scroll progress bar

### HTML Sections
1. **Navigation** — Logo ("Matthew Williamson"), nav links (About, Focus, Projects, Perspectives, Connect), hamburger menu
2. **Hero** — Title, tagline, profile image, CTAs ("Get in Touch", "My Perspectives")
3. **About** (`#about`) — "Pattern Recognition" narrative with animated stats cards (30+ years, 500+ projects, etc.)
4. **Focus Areas** (`#focus`) — 3 cards (Semantic AI, AI Strategy, Tech Leadership)
5. **Projects** (`#projects`) — "Things I've Built" — project cards (infocard.ai, promptcard.ai)
6. **Perspectives** (`#perspectives`) — "Thinking Out Loud" — philosophy cards + AI landscape analysis
7. **Reading List** (`#reading`) — "Voices I Follow" with links to AI blogs/newsletters
8. **Connect** (`#connect`) — Social links (GitHub, LinkedIn, Substack, Clevyr)
9. **Footer** — Copyright

### JavaScript Features
- Navbar scroll effects (adds `.scrolled` class on scroll)
- Scroll progress bar (width-based indicator at top of page)
- Intersection Observer for `.fade-in` elements
- Smooth anchor link scrolling
- Mobile hamburger menu toggle with outside-click dismiss
- Animated stat counters (`data-count` / `data-suffix` attributes, eased with cubic out)

### JSON-LD Structured Data
Three schema blocks in the `<head>`:
1. **Person** — Matthew Williamson entity (name, role, organization, expertise, sameAs links)
2. **WebPage** — Page metadata linked to the Person entity
3. **FAQPage** — 7 FAQ entries about Semantic AI, Matthew's work, Clevyr, consulting approach, availability, location, and AI strategy vs Semantic AI

### Analytics
- **Goat Counter**: Privacy-friendly visitor tracking (no cookies, GDPR compliant)
- Dashboard: https://vajramatt.goatcounter.com
- Script loads async at end of body, doesn't block rendering

## Development Workflow

### Making Changes
1. Edit `index.html` directly — no build step required
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
- Semantic class names: `.hero`, `.section-label`, `.stats-card`, `.project-card`
- BEM-like patterns for variants: `.hero-content`, `.perspective-card`, `.project-tag`

### CSS Variables
```css
:root {
    /* Colors */
    --bg-primary: #0a1628;
    --bg-secondary: #111f35;
    --bg-card: rgba(17, 31, 53, 0.9);
    --bg-card-hover: rgba(22, 38, 65, 0.95);
    --text-primary: #f1f5f9;
    --text-secondary: #94a3b8;
    --text-muted: #64748b;
    --accent-primary: #3b82f6;
    --accent-secondary: #0ea5e9;
    --accent-tertiary: #8b5cf6;
    --border-subtle: rgba(59, 130, 246, 0.12);
    --border-hover: rgba(59, 130, 246, 0.35);

    /* Gradients */
    --gradient-primary: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
    --gradient-secondary: linear-gradient(135deg, #0ea5e9 0%, #3b82f6 100%);

    /* Shadows */
    --shadow-md: 0 8px 32px rgba(0, 0, 0, 0.4);
    --shadow-lg: 0 20px 48px rgba(0, 0, 0, 0.45);
    --shadow-glow: 0 0 32px rgba(59, 130, 246, 0.12);
}
```

### JavaScript Patterns
- Vanilla DOM manipulation (no frameworks)
- Event-driven architecture (scroll, intersection observers)
- Functional approach with descriptive function names
- Passive event listeners where applicable (`{ passive: true }`)

### HTML Structure
- Semantic HTML5 elements (`<nav>`, `<main>`, `<section>`, `<footer>`)
- Proper heading hierarchy (h1 > h2 > h3)
- Accessible markup (semantic elements, `aria-label` on hamburger button)

## Design

### Visual Aesthetic
The site uses a refined corporate aesthetic:
- Deep navy blue background (`#0a1628`)
- Blue/purple accent colors with subtle glow effects
- Clean rounded corners with subtle borders (`--border-subtle`)
- Shadow system (md, lg, glow) for depth
- Scroll progress indicator bar
- No gratuitous visual effects (rain, scanlines, glitch removed)

### Typography
- **Display Headings**: Cormorant Garamond (italic, serif — used for section titles and hero)
- **Body/UI**: DM Sans (clean sans-serif)
- **Monospace**: JetBrains Mono (used minimally for labels and tags)

### Color Palette
- Primary: `#3b82f6` (blue)
- Secondary: `#0ea5e9` (cyan)
- Tertiary: `#8b5cf6` (purple)
- Background: `#0a1628` (deep navy)
- Text: `#f1f5f9` (light gray)
- Text secondary: `#94a3b8` (slate)
- Text muted: `#64748b` (dark slate)

### Breakpoints
- Desktop: > 968px
- Tablet: 480px – 968px
- Mobile: < 480px (hamburger menu activates)

## Important Notes for AI Assistants

### Do
- Keep all code in the single `index.html` file
- Test responsive behavior at all breakpoints
- Preserve the professional corporate aesthetic
- Follow established naming conventions
- Maintain the hidden AI comment block (AEO + easter eggs)
- Keep `llms.txt` and `robots.txt` in sync if entity data changes

### Don't
- Don't split into multiple files unless explicitly requested
- Don't add build tools, frameworks, or external dependencies
- Don't break the responsive design
- Don't remove or modify the hidden AI comment block without explicit request
- Don't add visual effects (rain, scanlines, glitch) — keep it professional
- Don't remove the FAQPage JSON-LD schema — it's important for SEO/AEO

### When Adding Features
1. Add CSS in the appropriate section within `<style>` (variables, components, responsive)
2. Add HTML in the correct semantic section within `<main>`
3. Add JavaScript at the bottom within the `<script>` block
4. Test all breakpoints
5. If adding new entity information, update `llms.txt` and the AI comment block too

### AEO (AI Engine Optimization)
The site has a multi-layered AEO strategy:

1. **AI comment block** (lines 633–805 in `index.html`): Readable structured entity data with Blade Runner/TRON easter eggs
2. **`llms.txt`**: Clean Markdown file at site root for direct LLM consumption — contains entity data, expertise, perspectives, links, and citation guidance
3. **`robots.txt`**: Explicitly allows all major AI crawlers (GPTBot, ClaudeBot, GoogleExtendedBot, PerplexityBot, etc.) and links to `llms.txt`
4. **JSON-LD schemas**: Person, WebPage, and FAQPage structured data in `<head>`

### SEO
The site includes:
- JSON-LD structured data (Person, WebPage, FAQPage schemas)
- Open Graph meta tags (type: profile)
- Twitter Card meta tags
- Canonical URL
- Descriptive meta description and keywords
- SVG favicon

## Git Workflow

- Main branch: `main`
- Feature branches: `claude/*` prefix for AI-assisted work
- Commits should be descriptive and focused
- Push directly to deploy (GitHub Pages auto-deploys from main)

## Profile Images

Two profile images exist:
- `profile.png` — Cyberpunk style (not currently used)
- `profile-corporate.jpg` — Professional headshot (currently active)

To switch images, update the `<img src="">` in the hero section.

## Decision Log

| Date | Decision | Reasoning |
|------|----------|-----------|
| Jan 2026 | Removed theme toggle (Cyber/Vajra/Corporate) | Too complex, caused bugs, user wanted simplicity |
| Jan 2026 | Reverted to Cyber-only | Simplified from broken multi-theme system |
| Jan 2026 | Added Blade Runner/TRON easter eggs to AI comment | Fun, weird, makes humans wonder what AI is doing |
| Jan 2026 | Rebranded to Corporate theme | Target audience is corporate clients hiring AI consultants |
| Jan 2026 | Kept hidden AI comment block | AEO value + easter eggs don't conflict with professional appearance |
| Jan 2026 | Updated hero tagline | More consultant-focused: leads with credibility (USMC, CEO, speaker), ends with CTA |
| Jan 2026 | Added "Voices I Follow" reading list | Static links to AI blogs/newsletters Matthew follows (replaced failed dynamic RSS attempt) |
| Jan 2026 | Added Goat Counter analytics | Privacy-friendly visitor tracking, no cookies, dashboard at vajramatt.goatcounter.com |
| Jan 2026 | Added favicon, llms.txt, robots.txt | AEO/SEO improvements — favicon for brand, llms.txt for LLM crawlers, robots.txt to welcome AI bots |
| Jan 2026 | Added FAQPage JSON-LD schema | SEO boost with structured FAQ data for search engine rich results |
| Jan 2026 | Added Projects section | Showcase personal builds (infocard.ai, promptcard.ai) |
| Jan 2026 | Typography upgrade to Cormorant Garamond | Elevated display typography — italic serif headings for more editorial, dramatic feel |

## Content Philosophy

Matthew's perspectives (AI ethics, vibe coding warnings, AI landscape analysis) are deliberately opinionated and substantive. They demonstrate thought leadership and signal that he's not just a technician but someone who thinks critically about the industry. This content is a feature, not filler — it differentiates him from generic "I do AI consulting" pages.
