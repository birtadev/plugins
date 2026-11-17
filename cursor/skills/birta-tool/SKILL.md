---
name: birta-tool
description: "Build an interactive tool — a pricing or ROI calculator, a unit converter, a quiz with scoring, a small browser game, a prototype people can try — as one static HTML page where everything runs in the browser and the result follows the reader's inputs, and publish it to Birta so people try it by link and reviewers pin remarks to it. Use whenever the user asks for a calculator, estimator, converter, simulator, quiz, test, assessment, game, playable demo, interactive prototype or \"something people can try\", whether or not they say where to host it. Not for a feature of the user's own app."
---

# Interactive tools on Birta

A tool page gives the reader one answer, one score or one win they could not get
from reading. It must be usable in the first ten seconds: the goal is obvious, the
controls are few, the result shows without a submit step. There is no backend on
Birta: the whole thing runs in the browser from one HTML page, and reviewers leave
remarks on it like on any other page.

## Ask before you build

Ask only what the user has not said; keep to the questions that change the result.

- Who uses it, and what decision or outcome do they leave with? One sentence.
- The logic: the formula, rates and assumptions; the questions, answers and scoring
  rules; the rules of the game. Ask for the user's own numbers and sources; never
  invent a benchmark or a "typical" value and present it as fact.
- Which inputs the reader must set, and which may start at a sensible default.
- What happens after the result: nothing, a shareable link, or a lead form.

## What the page contains

| Part | Must contain |
| --- | --- |
| Head | The tool's name as the title and one line on what it answers; no manual |
| Controls | Few inputs, each with a label, a unit, a default and a plausible range |
| Result | The headline number, score or state, large, with units, updated instantly |
| Breakdown | How the result was reached: formula, assumptions, per-answer feedback |
| Actions | Reset to defaults, copy link, restart; one next step at most |
| Notes | Sources of rates and benchmarks, limits of the model, the "as of" date |

A quiz adds: an intro with the length and what the reader gets, one question at a
time with progress, a result tier with a title and a short reading written for that
band, and a retake. A game adds: the goal and the controls on screen before play,
the play area, score and best score, and a restart one tap from "game over".

## Craft rules

- Compute as the reader types or drags; no Calculate button. A result must follow a
  slider within a tenth of a second; debounce only a genuinely slow computation.
- Pair a slider with a number field for exact values; show min and max; mark the
  default. Use `<input type="number">` with `min`, `max`, `step` and `inputmode`.
- Every input has a `<label for>`. Prefer native controls to custom widgets: they
  bring keyboard support for free. Enter submits an answer, arrows move a slider or
  a player, Escape pauses. Nothing works only on hover or only with a mouse.
- Show the work: the formula in words with the reader's numbers substituted, the
  assumptions as a list, benchmark sources named. A result the reader cannot defend
  to a colleague is decoration.
- Validate inline: say what is wrong and what range is accepted, next to the field,
  never in an alert. Never clear the reader's inputs on an error.
- Put the inputs in the URL `#` fragment as short keys (`#price=49&seats=12`) and
  read them on load, so a copied link reproduces the scenario. Keep it under 2,000
  characters and keep anything private out of it: whoever has the link reads it.
  Use `localStorage` only for conveniences such as a best score or an unfinished
  quiz, and work when it is unavailable.
- Give the result container `aria-live="polite"` so a changed result is announced;
  a quiz announces the verdict of each answer the same way.
- Tap targets at least 44×44 px, controls stacked at phone width. A game takes
  touch as well as keys, with on-screen buttons where keys are the only input, and
  fits its canvas to the viewport.
- Game feel: instant restart with no menus, failure explained on the game-over
  screen, one `requestAnimationFrame` loop cancelled before a restart, a pause when
  the tab is hidden, and no essential information carried by motion alone.
- Quiz feedback: say whether an answer was right and why before moving on; map
  score bands to distinct result tiers, each with its own text, and never a tier
  that reads as a sales pitch.
- Do not gate the result behind an email. A lead form sits after the result and
  offers something the result does not already give.
- Prefer one tool that does one thing well to a page of tabs; split the rest into
  linked pages.

## Build it on Birta

- HTML (`index.html`); Markdown pages drop scripts. For page layout, type and dark
  mode, follow `birta-design`; for the text, `birta-anti-slop-writing`; for a
  result chart, `birta-charts`; for a diagram of the model, `birta-diagrams`.
- One page, one state: screens and scenarios route through `#` only; any other
  path is "page not found" on reload.
- Keep the shell static and give each part a stable `id`: `id="inputs"`,
  `id="result"`, `id="breakdown"`, `id="question-3"`, `id="tier-high"`. Write every
  question, answer, tier text and assumption into the HTML; scripts show, hide and
  fill numbers into these elements, they never create them. Remarks attach to
  static elements and may lose their place on ones a script builds.
- Vanilla JS by default. Load a library from a CDN only when it earns its place (a
  physics engine, a chart that must zoom), pinned to an exact version, and keep the
  page under 2 MB. No build step and no framework runtime for a form and a formula.
- Keep a long question bank or rate table in a `data.json` next to the page when
  several tools share it; updating the data is a new version.
- Birta serves no audio or video files: synthesise game sounds with the Web Audio
  API or skip them, and start muted.
- A lead form after the result is declared with `create_form` first and written
  from the intake contract it returns; the `birta-manage` skill covers it.
- Publish with `publish_version`: the address stays the same for every version, so
  a shared `#` link keeps working after a fix.

## Check before publishing

- Defaults produce a sensible result; extremes (0, max, empty) do not break the
  layout or show `NaN`.
- Two scenarios recomputed by hand match the page.
- Keyboard only: reach every control, change every value, finish the quiz, play
  the game, restart.
- Phone width and dark mode: sliders usable with a thumb, no sideways scroll.
- The copied link opened in a fresh tab shows the same inputs and result.
- Every part someone may comment on has a stable id, and its text is in the source.
