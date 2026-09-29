# Frontend University Class

Coursework for a front-end web development class. Each folder is one chapter of notes and
practice files, ordered from plain HTML up to modern CSS layout. Everything is static — no
build step, no dependencies, no framework.

## Chapters

| Chapter | Folder | Topic | Files |
| ------- | ------ | ----- | ----- |
| 1 | `Chapter1/` | HTML basics: tables, forms, iframes, images | `aboutBegin.html`, `Form.html`, `iframe.html`, `Practice.html`, `CV_withHTML.html` |
| 2 | `Chapter2/` | CSS basics: selectors, colors, units, the cascade | `cvWithHtml.html`, `index.html`, `style.css` |
| 3 | `Chapter3_CSS_Layout/` | Responsive layout: CSS Grid, Flexbox, media queries | `Responsive.html`, `responsive.css` |

## Getting started

Open any `.html` file directly in a browser, or serve the folder locally if you prefer
relative paths and dev tools:

```bash
npx serve .
```

To review the responsive behaviour in Chapter 3, open `Chapter3_CSS_Layout/Responsive.html`
and resize the window (or use device emulation in DevTools) across these widths:

| Min width | Device | What changes |
| --------- | ------ | ------------ |
| base | mobile | Single column everywhere, nav wraps under the brand, 1rem gutter |
| `40rem` (640px) | tablet | Hero becomes 2 columns, card grid goes 2-up, nav sits in a row |
| `48rem` (768px) | laptop | Sidebar moves beside the main content and becomes sticky |
| `64rem` (1024px) | desktop | Card grid goes 4-up, hero gap widens |
| `80rem` (1280px) | wide | Container maxes out at `75rem` and centres |

## Chapter 3 — Responsive layout page

`Responsive.html` + `responsive.css` is a single self-contained exercise page that shows how
the two layout systems divide the work:

- **CSS Grid** for two-dimensional page structure — the hero (`grid-template-columns`), the
  card and stats grids (`repeat(auto-fit, minmax(15rem, 1fr))`, so they re-flow with no
  per-breakpoint column counts), and the content + sidebar split.
- **Flexbox** for one-dimensional component internals — the header bar, the nav and toolbar
  rows (`flex-wrap: wrap` plus `gap`), card bodies, and `margin-inline-start: auto` to push
  a badge to the far edge.
- **Media queries** only where a layout genuinely cannot be expressed by `auto-fit` — the
  sidebar position and the hero track ratio.
- **`clamp()` for fluid type**, so headings scale continuously instead of jumping at a
  breakpoint.
- **Custom properties** in `:root` for the palette, spacing scale and container width.

Supporting details worth knowing:

- Mobile first — each media query only *adds* layout, which keeps the base CSS small.
- No horizontal page scroll at any width; the wide breakpoint table scrolls inside its own
  `.table-wrap` instead of stretching the page.
- Accessibility: semantic landmarks, a skip link, visible `:focus-visible` outlines,
  `aria-label` on the nav, and `prefers-reduced-motion` support.
- `prefers-color-scheme: dark` and a small print stylesheet are included.
- The four `.btn` elements in the toolbar are `<button>`s with no behaviour attached — they
  are there to demonstrate wrapping, not functionality.

## Conventions

- Static files only, grouped by chapter folder.
- CSS lives in a sibling `.css` file once a page grows past a few rules; Chapter 1 and the
  Chapter 2 CVs use inline `style` attributes to keep the focus on HTML structure.
- Custom properties are preferred over repeated literal values once a stylesheet has more
  than one page-level section.
- Paths and asset references are relative, so a chapter folder can be opened or moved on its
  own.
