---
name: birta-charts
description: "Build charts, KPI tiles and dashboards for pages people will read — reports, investor updates, analytics summaries, research results — choosing the right chart for the question, drawing it to scale from real numbers, and keeping it readable in light and dark mode, on phones and for reviewers who comment on it. Use before writing any chart, graph, sparkline, stat tile or dashboard for a page that will be published or shown to people."
---

# Charts and dashboards on Birta pages

A chart answers one question with numbers. Decide the question first, then the
chart. Use only real numbers from the user or a cited source; if you must show
sample data, label it as a sample on the chart itself.

## Pick the form

| Question | Chart |
| --- | --- |
| How do categories compare? | Horizontal bars, sorted |
| How did it change over time? | Line; columns for few periods |
| What is it made of? | Stacked bar or a single 100% bar |
| How is it spread out? | Histogram or dot plot |
| How do two measures relate? | Scatter plot |
| One number that matters | A stat tile with its change and period |

Avoid pies with more than three slices, 3D, dual y-axes and decorative gauges.
A table beats a chart when the reader needs exact values.

## Draw it honestly

- One scale places every mark, tick and label. Bars start at zero. Ticks are round
  values the data actually reaches.
- Put the takeaway in the title ("Signups doubled after the March launch"), and the
  units, period and source in the subtitle or a footnote.
- Label lines and bars directly instead of using a legend when there are few
  series. Format numbers for people: `12.4k`, `$3.1M`, `+18%`, with tabular figures.
- Keep marks, labels and edges clear of each other and inside the chart's bounds.

## Color

- One accent color for the series that matters, neutrals for context. A categorical
  palette of at most six distinguishable colors, used in the same order everywhere.
- Good, warning and critical colors carry status only, never series identity.
- Define every chart color as a CSS custom property and redefine it under
  `@media (prefers-color-scheme: dark)`; axis text and gridlines also come from
  tokens, so the chart reads in both themes. Never rely on color alone: vary shape,
  dash or labels too.

## Build it for Birta

- Prefer static SVG in the page's HTML, generated while you write the page. It
  loads complete without scripts, scales with `viewBox`, follows theme tokens, and
  every bar or point can carry an `id` that a reviewer's remark attaches to.
  Birta cannot follow a chart that a script draws at runtime from version to
  version, so its remarks may lose their place.
- Use a charting library (for example Chart.js, ECharts or D3 from a CDN, pinned to
  an exact version) only when the chart needs real interaction such as zoom or
  brushing. Give its container an `id`, a fixed aspect ratio and a caption, and put
  the same numbers in a `<details>` table below as a fallback.
- Keep the data in a JSON file next to the page when several charts share it.
  Updating the numbers is a new version: edit the data, then publish.
- Size charts with `width: 100%` and an aspect ratio; at phone width, switch to
  horizontal bars or fewer ticks rather than shrinking text below 12px.

## Dashboards

Put the summary first: three to five stat tiles with value, change and period, then
the charts that explain them, then detail tables. Show state in form as well as in
numbers: a chip or a colored marker for anything that needs attention. Align tiles
on one grid with the same padding and baselines. A dashboard on Birta is a
snapshot: show its "as of" date prominently.

For page layout and type, follow the `birta-design` skill.
