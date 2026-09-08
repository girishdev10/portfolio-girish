# Girish M — Portfolio Website

A single-file, self-contained portfolio site (`Index.html`) with a dark "blueprint / technical grid" theme. No build tools, frameworks, or external dependencies required — just open the file in a browser.


## How it's built

Everything lives in **one HTML file**:
- `<style>` — all CSS (colors, layout, animations)
- `<body>` — all page content, split into `<section>` blocks
- `<script>` — all interactivity (scroll effects, typing animation, reveal-on-scroll)

There is no separate CSS/JS file and no backend — it's a static page you can host anywhere (GitHub Pages, Netlify, or just double-click to open locally).

## Page structure

The page is one long scrollable document, broken into numbered sections (each has a `<div class="fig-label">` with a number like `00`, `01`, `02`...):

| # | Section id | Content |
|---|-----------|---------|
| 00 | `#photo` | Portrait photo |
| 01 | `#about` | About Me summary |
| 02 | `#education` | Degree, year, college |
| 03 | `#skills` | Programming languages, tools, core subjects (tag chips) |
| 04 | `#project` | Featured project card with a link to its GitHub repo |
| 05 | `#interests` | Areas of interest (grid of items) |
| 06 | `#goals` | Learning goals |
| 07 | `#strengths` | Personal strengths (grid of items) |
| 08 | `#philosophy` | Personal philosophy quote |
| 09 | `#vision` | Future vision quote |
| 10 | `#contact` | Contact links (Email / GitHub / LinkedIn) |

A sticky header at the top (`GIRISH M` + nav links) stays visible while scrolling, so visitors can jump between sections (Photo, About, Education, Skills, ...).

## Key design/interaction details

- **Contact links (`#contact`)** — each is a full-width row showing a label (Email/GitHub/LinkedIn), the actual handle (e.g. `girishkannan193@gmail.com`, `@girishdev10`, `Girish M`), and a `→` arrow. Clicking opens `mailto:` for email, or the profile in a new tab for GitHub/LinkedIn. There is intentionally **no contact form** — it's link-only, so there's no backend needed to receive messages.
- **Project link (`#project`)** — styled as a small pill/button ("View GitHub Repository →"), not a heading, so it visually reads as a link rather than a page title.
- **Footer** — centered copyright line (`© 2026 Girish M · JCET, Lakkidi`) with a small glowing dot divider, separated from the page by a dashed top border.
- **Skill tags** — each skill group (Languages / Tools / Core Subjects) uses inline SVG icons (defined once in a hidden `<svg><defs>` block near the top of `<body>`) referenced via `<use href="#icon-...">`.

## JavaScript behavior

All script logic is in the single `<script>` block near the end of the file:

1. **Scroll-based header/UI updates** — an `onScroll` listener (throttled, passive) updates styling as the user scrolls.
2. **Typing animation** — `typeAll()` / `nextLine()` animate text (e.g. in the header) to look like it's being typed out character by character.
3. **Reveal-on-scroll** — an `IntersectionObserver` watches elements with class `.reveal` (cards, project blocks, quotes, grids) and fades/slides them in as they enter the viewport. Falls back to showing everything immediately if `IntersectionObserver` isn't supported or the user has "reduced motion" enabled.

## How to edit content

- **Text content**: find the relevant `<section id="...">` block and edit the text directly.
- **Contact info**: update the `mailto:`, GitHub, and LinkedIn URLs plus their `<span class="value">` text inside `#contact`.
- **Project repo link**: update the `href` on the `.project-link` anchor inside `#project`.
- **Photo**: the portrait is embedded directly as a Base64 data URI inside the `<img>` tag in `#photo` — to change it, replace that `src` with a new Base64 string (or swap to a normal image file path/URL).
- **Colors/theme**: CSS custom properties (`--red`, `--cyan`, `--gold`, `--text`, `--surface`, etc.) are defined near the top of `<style>` — change these to re-theme the whole site.

## Hosting

Since it's a static single file with no backend:
- **GitHub Pages**: push `Index.html` (rename to `index.html`) to a repo and enable Pages.
- **Netlify/Vercel**: drag-and-drop deploy.
- **Locally**: just open the file in any browser.

No server, database, or build step is required.
