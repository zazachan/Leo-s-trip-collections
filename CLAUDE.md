# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A personal collection of static HTML travel itinerary pages (Traditional Chinese, zh-TW). Each trip is a single self-contained HTML file with all CSS and JavaScript inlined — no build tools, no package manager, no dependencies.

## File Structure Convention

Each trip lives in its own folder named `YYYYMMDD CityName/index.html`:

```
20260518 Seoul/index.html
```

## Architecture of Each Itinerary Page

Every `index.html` is fully self-contained:

- **CSS**: Embedded in `<style>` — uses a Morandi (莫蘭迪) muted color palette. Day colors follow a 4-color scheme: foggy blue (`d1`), camel pink (`d2`), sage green (`d3`), mauve purple (`d4`).
- **HTML structure**: `.container` → `header` → `.tip-box` → `.map-dashboard` (zone overview grid) → `.day-section` blocks → `footer`
- **JavaScript**: Single `toggleDay(dayId)` function that collapses/expands `.day-section` elements by toggling a `collapsed` CSS class.
- **Navigation buttons**: Each location has a pair of `<a>` links — Google Maps (`btn-google`) and Naver Maps (`btn-naver`, preferred for in-Korea navigation).
- **Responsive**: CSS media query breakpoint at 520px (grid columns) and 600px (body font size, container padding/radius).

## Development

No build step — open `index.html` directly in a browser to preview. To serve locally:

```powershell
# Python (if installed)
python -m http.server 8080
# Then open http://localhost:8080/20260518%20Seoul/
```

## Conventions When Adding a New Trip

1. Create folder `YYYYMMDD CityName/` and copy an existing `index.html` as the template.
2. Keep all CSS and JS inline — do not introduce external files or CDN links.
3. Maintain the Morandi color palette; add a new day color variable if the trip exceeds 4 days.
4. Every location block must include both a Google Map and a Naver Map link.
5. The `.tip-box` at the top should note any special scheduling constraints (holidays, lottery queues, etc.).
