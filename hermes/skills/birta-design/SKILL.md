---
name: birta-design
description: "Design and build a page to publish — a website, landing page, presentation, report, document, portfolio or interactive tool — so it looks deliberate, works on phones and in dark mode, and keeps reviewers' remarks attached across versions in Birta. Use whenever you write or restyle HTML, CSS or a Markdown page that will be published or shown to people by link, whether or not Birta is named."
---

# Design a page for Birta

Everything you publish to a Birta project opens at its address in a browser, and
people review it right on the page. Build it so it reads well at first glance,
works on any screen, and survives the review loop: remarks pinned to elements,
new versions at the same address.

The user's own words win over everything here, then the project's existing
styles, then your choices. When you continue an existing project, read its files
first (`list_files`, `read_file`) and keep its look unless asked to change it.

## Pick the format

- **Markdown** (`index.md`) for a text document: a memo, a guide, a plan, notes.
  Birta renders it as a readable page with heading anchors, tables, `<details>`,
  images and ```` ```mermaid ```` diagrams, and shows the front matter as a table.
  Scripts, forms and style blocks are not drawn. Do not convert such a document to
  HTML just for its markup.
- **HTML** (`index.html`) when layout, visual identity or interaction matter: a
  website, a landing page, a presentation, a dashboard, a tool, a game. A page
  with a form must be HTML: Markdown pages drop forms.

Link pages with ordinary relative links. A single-page app routes through `#`:
any other path returns "page not found" on reload.

## Decide the treatment

Read what the page is for before designing.

- **Working documents** (a report, a plan, a proposal, a status page) get a calm,
  polished treatment: a clear type hierarchy, considered spacing and a deliberate
  palette. No oversized hero, few flourishes.
- **Pages people keep or show** (a landing page, a portfolio, an event page, a
  game) get an editorial treatment: a point of view specific to the subject, one
  bold idea, everything around it quiet.

When unsure, a well-composed calm page is always acceptable; an overdone one is not.

## Ground it in the subject

Name the subject, the audience and the page's one job. Take materials, colors and
vocabulary from the subject's own world and use its real units, terms and
conventions. Use the user's real content; never lorem ipsum. Where you need
example data, mark it as an example.

Generated pages tend to look alike: a cream background with a serif and a
terracotta accent, near-black with one neon accent, a purple-to-blue gradient
hero, Inter everywhere, emoji as section icons, everything centered, the same
rounded card on every block. Avoid these defaults unless the user asks for one.

## Build it to survive review

Reviewers pin remarks to elements, and Birta carries each remark to the same
element in the next version.

- Give every section and every block someone may comment on a stable, unique
  `id` (`id="pricing"`, `id="step-2"`). An element with an id keeps its remarks
  even when its text, look or position changes.
- Put content in the static HTML. Birta cannot follow an element that a script
  draws at runtime from version to version, so its remarks may lose their place.
  Use scripts for behavior, not to generate the readable content.
- Apply feedback by editing the element in place (`edit_file`, `replace_lines`)
  rather than regenerating the page; keep ids when you rewrite a block.
- Birta adds its review controls and, unless the owner hid it, a small "made
  with Birta" mark at the end of `<body>`. Do not set a nonce- or hash-based
  Content-Security-Policy, or they will not appear, and do not rely on your own
  element being the last child of `<body>`. A page over 2 MB gets neither, so
  move large inline data and images into separate files.

## Page skeleton

Write a complete document: `<!doctype html>`, `<html lang="…">` in the content's
language, `<meta charset="utf-8">`, `<meta name="viewport"
content="width=device-width, initial-scale=1">`, a `<title>` that names the page
(a short specific noun phrase, not a sentence), a meta description, and Open
Graph title, description and image for link previews: people share this address.

## Typography

- Pair a display face used with restraint and a readable body face; add a mono or
  utility face only for data or code. Self-host `woff2` files next to the page, or
  load Google Fonts, and always declare a fallback stack.
- Set one type scale and keep to it. Keep running text near 65 characters wide.
  Balance headings (`text-wrap: balance`), give body text generous line height,
  add slight letter spacing to uppercase labels.
- Use `font-variant-numeric: tabular-nums` where digits line up.

## Color and themes

- Define every color as a CSS custom property on `:root`, 4–6 named tokens plus
  semantic colors (success, warning, danger) kept apart from the accent.
- Design dark mode too: redefine the tokens inside
  `@media (prefers-color-scheme: dark)` and set `color-scheme: dark` there. Give
  `body` an explicit background. Never use a literal color that works in one theme
  only. A page that deliberately commits to one look may skip dark mode, but it
  still sets every color explicitly.
- Tint neutrals slightly toward the accent instead of using flat mid-grey.

## Layout

- Lay out groups with flex or grid and `gap`, not margins on every element.
- It must work at 360px: a side gutter of at least 16px, rows that wrap or stack,
  `min-width: 0` on flex and grid children that hold text, `max-width: 100%` on
  media. The page never scrolls sideways; only a wide table, code block or
  diagram scrolls inside its own `overflow-x: auto` container.
- Size a hero to its content, not to `100vh`. Everything meant to be read is
  visible once the page loads; animate in from a visible state, never from
  `opacity: 0` waiting for a scroll.
- Keep repeated items consistent: same padding, edges and baselines. Use borders,
  shadows and fills to set one element apart, not on every block.
- Use numbering, eyebrows and dividers only when they carry meaning, such as a real
  sequence.

## Presentations

Build a deck as one HTML page with one `<section id="slide-N">` per slide: keyboard
and swipe navigation, the current slide in `location.hash` so a link opens it, and
a readable printed or scrolled fallback when scripts fail. Each slide is a
separate target for remarks.

## Files and assets

Birta serves web files only: HTML, CSS, JS, JSON, SVG, raster images (PNG, JPEG,
WebP, AVIF, GIF), fonts, Markdown, text, WASM and ZIP downloads. Video, audio and
PDF are not served, nor are `.htm` and `.csv`: name pages `.html`, ship data as
`.json`, and host media and PDFs elsewhere with a link. One file is at most
25 MB and a version holds at most 2,000 files. Prefer local copies of images and
fonts over hotlinks; every external host is a dependency the page can lose. Pin
any library loaded from a CDN to an exact version.

## Craft and copy

- Close every element, quote attributes, show visible keyboard focus, give images
  real `alt` text, and respect `prefers-reduced-motion`.
- Write copy from the reader's side: plain words, active voice, buttons that say
  what happens. Avoid filler phrases and dashes used as decoration.

## Check, then publish

Before publishing, open the page once in a browser if you can: desktop and phone
widths, light and dark. Fix what you see in one pass, then publish with
`publish_version` and give the user the project address. Further polish comes from
the user's remarks on the page.

For diagrams, use the `birta-diagrams` skill; for charts, KPIs and dashboards, use
`birta-charts`. Forms that collect leads are declared through Birta first; the
`birta-manage` skill covers them.
