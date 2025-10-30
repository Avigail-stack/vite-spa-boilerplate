# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Vite-based single-page application for NeuroWave AI, a fictional brain waves signal reader product. The project is a marketing/landing page built with vanilla JavaScript and modern CSS.

## Git Workflow

After each code change, commit and push it immediately.

## Development Commands

All commands must be run from the `vite-spa-boilerplate` directory:

```bash
# Start development server (runs on http://localhost:5173/)
cd vite-spa-boilerplate && npm run dev

# Build for production
cd vite-spa-boilerplate && npm run build

# Preview production build
cd vite-spa-boilerplate && npm preview
```

## Architecture

### Entry Points
- **vite-spa-boilerplate/index.html**: Root HTML file that mounts the app to `#app` div and loads `/src/main.js`
- **vite-spa-boilerplate/src/main.js**: Application entry point that renders the entire page via innerHTML and sets up interactive features

### Code Structure

The application uses a **single-file approach** rather than component-based architecture:

- **src/main.js**: Contains all HTML markup (injected via innerHTML), smooth scroll navigation, intersection observer for scroll animations, and navbar scroll effects
- **src/style.css**: All styling using CSS custom properties (CSS variables), animations, and responsive design
- **src/counter.js**: Unused boilerplate file from Vite starter (can be removed)

### Design System

The application follows an Apple-inspired design language:

- **Color Palette**: Defined in CSS custom properties (`--color-primary`, `--color-accent`, etc.) in vite-spa-boilerplate/src/style.css:8-17
- **Typography**: Uses SF Pro Display/Text font stack with careful attention to font weights, letter spacing, and responsive text sizing via `clamp()`
- **Layout Pattern**: All major sections follow a consistent pattern: hero → feature sections (alternating light/dark backgrounds) → specs → pricing → footer

### Interactive Features

1. **Smooth Scroll Navigation**: Links with `href="#"` scroll smoothly to anchor targets (vite-spa-boilerplate/src/main.js:240-248)
2. **Scroll Animations**: Intersection Observer triggers `.visible` class on feature sections when they enter viewport (vite-spa-boilerplate/src/main.js:251-269)
3. **Navbar Scroll Effect**: Navbar gains `scrolled` class after 50px scroll for enhanced backdrop blur (vite-spa-boilerplate/src/main.js:272-285)
4. **CSS Animations**:
   - Brain wave visualization using animated lines (vite-spa-boilerplate/src/style.css:232-251)
   - Floating device mockup (vite-spa-boilerplate/src/style.css:211-214)
   - Pulsing AI chip visual (vite-spa-boilerplate/src/style.css:332-390)
   - Fade-in animations with staggered delays (vite-spa-boilerplate/src/style.css:709-739)

### Responsive Design

- Breakpoints at 768px and 480px (vite-spa-boilerplate/src/style.css:742-808)
- Uses CSS Grid with `auto-fit` for flexible layouts
- Typography scales with `clamp()` for fluid responsive text
- Mobile: Stacks columns, adjusts spacing, and simplifies navigation

## Key Implementation Patterns

### Adding New Sections
When adding new page sections to vite-spa-boilerplate/src/main.js:

1. Add HTML markup within the template literal (after line 237)
2. Add corresponding styles to vite-spa-boilerplate/src/style.css
3. If the section needs scroll animations, add it to the observer (vite-spa-boilerplate/src/main.js:266-268)

### Styling Conventions
- Use CSS custom properties for colors/theme values
- Follow Apple-style naming: `.hero-title`, `.feature-section`, `.spec-card`
- Animations use `cubic-bezier(0.16, 1, 0.3, 1)` for smooth, natural easing
- Hover effects typically include `transform: translateY()` and box-shadow

### HTML Structure Pattern
Most sections follow this pattern:
```html
<section class="[section-name]-section">
  <div class="[section-name]-content">
    <!-- content -->
  </div>
</section>
```

## Build Output

- Production builds output to `vite-spa-boilerplate/dist/` directory (gitignored)
- Assets are optimized and fingerprinted by Vite
- The build is purely static HTML/CSS/JS (no server required)