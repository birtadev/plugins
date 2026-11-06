---
name: birta-diagrams
description: "Decide when a page people will read needs a diagram and draw one that shows the real mechanism — flows, architectures, processes, timelines, org charts, comparisons — with Mermaid in Markdown or hand-built SVG in HTML, readable in light and dark mode and on phones. Use when a page that will be published or shown to people explains how something works or how parts relate."
---

# Diagrams on Birta pages

A diagram earns its place when the reader needs to see how parts relate: what
flows where, what depends on what, what happens in which order. If a sentence or a
short list says it as well, write the sentence.

## Decide what to draw

Start from the question the diagram answers, then pick the form:

| The reader needs to see | Draw |
| --- | --- |
| Steps and decisions | Flowchart, top to bottom or left to right |
| Who talks to whom over time | Sequence diagram |
| Parts of a system and their links | Boxes and arrows, grouped by boundary |
| States and what moves between them | State diagram |
| Events on a calendar | Timeline or Gantt |
| A hierarchy | Tree |
| Two or three options side by side | A table, not a diagram |

Draw the real thing: the actual names of services, people, steps and data, the
real direction of every arrow. A generic "Input → Process → Output" teaches nothing.
Keep one diagram to about a dozen nodes; split a bigger picture into an overview
and close-ups. Label arrows with what travels along them.

## In a Markdown page

Birta draws a ```` ```mermaid ```` code block in a Markdown page as a diagram; no
library is needed. Prefer this for documents.

- Use short node ids and quoted labels: `api["Billing API"]`.
- Set the direction deliberately (`flowchart LR` for pipelines, `TD` for
  hierarchies) and group with `subgraph` for boundaries.
- Leave styling to the renderer so the diagram follows the reader's theme; avoid
  hard-coded fill colors.
- Put a one-sentence caption before the diagram that says what to notice.

## In an HTML page

Birta does not render Mermaid inside HTML. Either hand-build inline SVG (best
control, no script, and every shape can carry an `id` that reviewers' remarks
attach to) or load Mermaid from a CDN pinned to an exact version. Prefer inline SVG
for anything that is central to the page.

For inline SVG:

- Set a `viewBox` and let the SVG scale: `width: 100%; height: auto`. Keep room
  inside the viewBox for the outermost labels.
- Take every color from the page's CSS custom properties (`fill: var(--fg)`,
  `stroke: var(--line)`), so the diagram follows light and dark mode. Give every
  shape an explicit fill, `none` included.
- Keep text at least 12px at the rendered size; at phone width that usually means
  a vertical layout. Wrap a diagram that cannot shrink in an `overflow-x: auto`
  container.
- Snap boxes to a grid, align centers, keep equal gaps, and route arrows with right
  angles or gentle curves that never cross labels. Define one arrowhead `<marker>`
  and reuse it.
- Use color for meaning only: one accent for the path that matters, neutral for the
  rest, the same color for the same kind of thing.
- Add `role="img"`, a `<title>` and a `<desc>` summarizing the diagram, and an `id`
  on the SVG and on its key groups.

## Before publishing

Check that every label is inside its box, nothing overlaps, arrows point the right
way, and the diagram reads in both themes and at phone width. For page layout and
type, follow the `birta-design` skill.
