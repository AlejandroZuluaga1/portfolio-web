# AGENTS.md

## Project Overview

Static, single-page HTML/CSS/JavaScript portfolio website. No build step, no npm, no framework. Browse as-is by opening `index.html` in a browser.

## File Structure

```
index.html              # All content and structure (223 lines)
assets/
  ├─ css/styles.css    # All styling (CSS variables for theming)
  ├─ js/main.js        # Vanilla JS interactions
  └─ img/              # Images and icons
```

## Critical Setup Facts

### External CDN Dependencies

These are loaded in the `<head>` of `index.html`. Agents must preserve them to avoid breaking functionality:

- **Remixicon 4.9.0** – Icon library (line 13)
- **Swiper 12** – Carousel for work section (line 16)
- **Typed.js** – Typing animation (not explicitly linked in head; check if dynamically loaded or missing)

### Styling System: CSS Variables

Color theming is controlled by a single CSS variable `--hue` in `assets/css/styles.css:21`:

```css
--hue: 110;  /* Default: green. Change to customize all colors */
```

All other colors derive from this hue using HSL. Don't edit individual color values—change `--hue` instead.

### Vanilla JavaScript Quirks

- `main.js:31-42` – Circular text animation uses DOM manipulation to rotate individual letters. Do not simplify without testing visually.
- `main.js:63-83` – Swiper carousel initialized with responsive breakpoints (540px, 1150px). Update these if changing layout.
- Menu toggle uses `show-menu` class; closing happens on nav link click (`main.js:23-28`).

### Content Location

All page content (text, headings, sections) is hard-coded in `index.html`. There is no CMS or data file. To change copy or structure, edit HTML directly.

## Common Agent Mistakes to Avoid

1. **Don't assume there's a build step.** There isn't. Changes to CSS/JS are live immediately; just refresh the browser.
2. **Don't break CDN links.** Removing or modifying `<link>` tags in `<head>` will disable icons, carousel, and typing animation.
3. **Don't move/rename asset files** without updating relative paths in `index.html` (e.g., `src="assets/img/home-img.png"`).
4. **Don't minify or bundle files.** The code is meant to be readable and simple; keep it plain.
5. **Don't edit individual color values in CSS.** Only change the `--hue` variable; everything else derives from it.

## Testing

Open `index.html` directly in a modern browser (Chrome, Firefox, Safari). No local server required. Test responsiveness using browser DevTools.

## Git Status

No `.git` directory. User can initialize version control if needed: `git init`.
