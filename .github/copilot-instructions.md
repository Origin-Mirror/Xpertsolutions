# Copilot Instructions for Xpertsolutions

## Project Overview
Xpertsolutions is a static website for a professional relationship solutions service. The site features a responsive, single-page design with embedded CSS and minimal dependencies. It's deployed via Jekyll on GitHub Pages (CNAME: `www.charlottexpertsolutions.com`).

## Architecture & File Organization
- **HTML Pages**: Standalone HTML files (`index.html`, `main.html`, `update.html`, `update 2.html`) with embedded `<style>` blocks—no separate CSS files are used
- **Brand Colors** (CSS variables in `:root`):
  - Primary: `#8b55a3` (purple), Secondary: `#f29c1f` (orange)
  - Light backgrounds: `#f6effa`, `#eadcf3` for gradient/accent elements
  - Text: `#111827` (dark), `#4B5563` (gray)
- **Note**: The file `<!DOCTYPE html>.css` is actually an HTML file with incorrect naming—treat as legacy/unused

## Key Patterns & Conventions
- **Responsive Design**: Mobile-first media queries at `max-width: 820px` toggle navigation with `.nav-toggle` button
- **Styling Approach**: All CSS is embedded in `<style>` blocks; use CSS custom properties for theming
- **Component Reuse**: Navigation, hero sections, and button styles are duplicated across pages—maintain consistency
- **Sections Use BEM-like Classes**: `.section-title`, `.container`, `.btn-primary`, `.btn-outline`

## Build & Deployment
- **Build System**: Jekyll (Docker-based)
  - Workflow: `.github/workflows/jekyll-docker.yml`
  - Command: `jekyll build --future` runs in `jekyll/builder:latest` container
  - Output: Generated to `_site/` directory on push to `main`
- **Domain**: Configured via `CNAME` file pointing to `www.charlottexpertsolutions.com`

## Common Tasks
- **Add/Update Pages**: Create `.html` file with full embedded style block and navigation. Copy from `index.html` structure.
- **Add Portfolio/Gallery Content**: Portfolio slideshow is in `index.html` with images from `work images/` folder. Each image is a separate slide. Modify `.slideshow-container` and JavaScript functions to customize.
- **Adjust Branding**: Modify CSS variables in `:root`—changes propagate across all pages
- **Responsive Adjustments**: Update media query breakpoints (currently `820px`) and mobile-specific rules in navigation

## Featured Implementations
- **Portfolio Slideshow**: Auto-rotating image gallery with prev/next buttons, slide counter, and dot indicators. Located in `#portfolio` section. JavaScript auto-advances every 6 seconds; can be modified in the `setInterval(nextSlide, 6000)` line.
- **Mobile Navigation**: `.nav-toggle` button shows/hides navigation menu on screens ≤820px. Toggle state managed via `aria-expanded` attribute.

## When Modifying Content
- Maintain consistent naming: Use proper filenames (avoid spaces in production files)
- Keep embedded CSS patterns consistent across all HTML files to ensure UX uniformity
- Test responsiveness at mobile breakpoint; navigation toggle is critical for UX
