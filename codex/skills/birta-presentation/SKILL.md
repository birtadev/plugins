---
name: birta-presentation
description: "Build a presentation — a pitch deck, a product, course or sales presentation, an internal update, a talk — as one HTML page of slides that opens in any browser and moves at the viewer's pace, and publish it to Birta so it has an address to share and viewers pin remarks to the slide they mean. Use whenever the user asks for a deck, slides, a pitch or a presentation, whether or not they say where it should live: a deck exists to be shown, and Birta gives it an address. Not for slides that are part of the user's own app."
---

# Presentations on Birta

A deck published on Birta is opened from a link, often with nobody presenting it.
Its job is to get one decision or action from the viewer: invest, buy, approve,
enroll, agree to the plan. Every slide either moves the viewer toward that or
goes to the appendix.

## Ask before you build

Ask only what the user has not already said, in one message:

1. Who opens it, and what should they do or decide after the last slide?
2. Presented live by the user, or read alone from the link? This sets density:
   a presented deck is sparse and keeps the detail in speaker notes; a reading
   deck carries full sentences and stands on its own.
3. How long: a slide count or the minutes it gets. Default to 10–12 slides for a
   pitch, 15–20 for a reading deck; longer belongs in an appendix.
4. What material exists: numbers, product screens, brand colors, a prior deck.
   Never invent figures; mark any example data as such on the slide.

## Shape of the deck

| Slide | Must contain |
| --- | --- |
| Title | The subject, who it is for, the date; one line that states the point |
| The claim | The whole argument in one sentence; the reader could stop here |
| Body, one idea each | An assertion as the title and the evidence below it |
| The ask | What the viewer does next, by when, how to reach the user |
| Appendix | Detail tables, methodology, extra numbers, anything asked for |

Body outlines by kind:

- **Pitch deck:** purpose, problem, solution, why now, market, competition,
  business model, traction, team, financials, the ask.
- **Product or course presentation:** who it is for, the outcome they get, what
  changes for them, how it works, proof, price or terms, the next step.
- **Internal update:** the headline status, what changed since last time, the
  numbers, risks and blockers, the decisions needed from the room.

Drop any slide the audience already knows. A deck under ten slides needs no
agenda slide.

## Craft rules

- One idea per slide. When a slide needs a second takeaway, split it; never
  shrink the type to fit.
- Title every slide with the assertion, not the topic: "Churn fell to 2% after
  onboarding", not "Churn". A viewer who reads only the titles gets the argument.
- Below the title put evidence, not bullets that restate it: one chart, one
  diagram, one screenshot, one quote with its source, one big number with its
  period. Every number carries its unit, period and source.
- Cut any line that takes more than five seconds to read on a presented deck.
  On a reading deck, write complete sentences and keep them short.
- Speaker notes hold what the user will say: one `<aside class="notes">` per
  slide, hidden in the slide view, shown in the scrolled view and on print.
- Keep one layout grammar across the deck (title position, margins, type scale),
  and vary the composition inside it: a chart slide, a quote slide, a two-column
  comparison, a single statement. Not the same card ten times.
- Use the subject's own vocabulary, screens and colors; no stock illustrations,
  no decorative icons beside each bullet, no slide that is only a logo.
- Put the ask on its own slide and repeat the contact at the end: a viewer who
  arrived by link has no presenter to turn to.
- For the text itself, follow `birta-anti-slop-writing`.

## Build it on Birta

Always HTML: a Markdown page cannot present. Follow the Presentations section of
`birta-design`: one `<section id="slide-N">` per slide, keyboard and swipe
navigation, the current slide in `location.hash`, and a readable scrolled fallback
when scripts fail. Ids start at `slide-1`; navigation follows the slides' order in
the DOM, not the numbers, so a slide inserted later takes a new id rather than
renumbering the rest, and remarks stay attached.

- Inside a slide, give each block someone may comment on its own id:
  `slide-4-chart`, `slide-4-note`, `slide-7-price`.
- Write slide content in the static HTML. Navigation is the script's only job.
- A slide fits one screen at 16:9 on a laptop, and stacks into a readable column
  at phone width; text never falls below readable size, a slide splits instead.
- For charts and KPI tiles, follow `birta-charts`; for flows, architectures and
  timelines, follow `birta-diagrams`; for layout, type, color and dark mode,
  follow `birta-design`.
- Send the viewer to a link that opens one slide (`#slide-8`) when a message
  points at a specific slide.
- If the ask collects something on the deck itself (book a call, request access,
  leave an email), declare the form with `create_form` first and write the markup
  from the contract it returns, as the `birta-manage` skill describes.
- Publishing, versions and reading remarks: follow the `birta-publish` skill;
  access and sharing: `birta-manage`.

## Check before publishing

- Reading only the slide titles tells the whole argument.
- Each slide has one idea, and nothing overflows the slide at 16:9 or at phone
  width, in light and dark mode.
- Every number has a unit, a period and a source; sample data is labeled.
- The ask and the contact are on their own slide.
- Notes are hidden in slide view and visible in the fallback.
- Keys, swipe and `#slide-N` links move through the deck; the page scrolls
  readably with scripts off.
- The title, description and link preview name the deck for people who get the
  link.
