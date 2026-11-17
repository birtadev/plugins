---
name: birta-portfolio
description: "Build a portfolio, personal site, CV page or case study for a designer, developer, writer, student or agency, so a hiring manager or client sees in half a minute who this is, what they did and how to reach them, and finds the thinking behind each piece (problem, approach, result); publish it to Birta so it has an address for a bio or an application. Use whenever the user asks for a portfolio, personal site, case study, project write-up, CV or résumé page, agency work page or client showcase, whether or not they say where to host it. Not for the about page of the user's own product."
---

# Portfolios and case studies on Birta

A portfolio is read by someone busy who decides in a few minutes whether to call.
It must answer, in this order: who is this, what kind of work, is it good, what
exactly did they do, and how do I get in touch. A case study is the proof: it shows
judgment, not just output. Everything that does not serve that decision goes.

## Ask before you build

Ask only what the user has not said; one short message, not a questionnaire.

1. Who should call after reading, and for what: a job (which role), freelance
   clients, agency leads, a school admission? This sets what to show first.
2. Which three to six pieces of work, and for each: what the problem was, what
   the user personally did, who else was on it, and what came of it. Numbers,
   quotes or links if they exist; "none" is a valid answer and is stated as such.
3. What can be shown: are any pieces under NDA, which images and links exist,
   and may the client be named?
4. Contact path: email, a form on the site, a calendar link, which profiles.

Do not ask about colors, fonts or layout; infer them from the work itself.

## Shape of the site

| Page or block | Must contain |
| --- | --- |
| Home, first screen | Name; what they do and for whom; what sets them apart; the strongest piece visible without scrolling; a contact link |
| Work list | 3–6 pieces, strongest and most recent first; per card: title, one-line outcome, role, year, a real image |
| Case study | Context in three lines (client or team, role, dates); problem; approach with the decisions and why; result; what they would do differently; links to the live thing or the code |
| About / CV | Track record; skills and tools as they relate to the target role; where they are based and how they work |
| Contact | One primary path, repeated at the end of every page |

A single page suits a short portfolio; separate pages per case study suit more
than four pieces or long write-ups. Either way the first screen of every page
names the person and offers a way to contact them.

## Craft rules

- Selection over volume. Six strong pieces beat twenty. Drop anything the user is
  not proud of, tutorials, clones, unfinished work and "coming soon".
- Say "I" and name the role. "We redesigned checkout" tells a reader nothing;
  "I owned the checkout flow; two engineers and a PM worked with me" does. Credit
  collaborators by name where allowed.
- Lead each case study with the result, like a news story, then explain how. A
  result is a number ("checkout completion +18% in six weeks"), a shipped link,
  a client quote with a name, or an honest "not measured".
- Show the decision, not the ritual. Two or three real choices with the option
  rejected and why beat a list of methods. Skip generic process diagrams.
- Pictures large enough to judge craft: full-width screens, real artifacts, no
  phone mockups of a tiny screen, no stock photos.
- Never invent numbers, clients or quotes. If the user has no outcome, write what
  shipped and what they learned; do not fill the gap.
- NDA work: keep the piece, strip the identifiers. Name the sector not the client,
  describe the direction of change not the figure, state in one line that details
  are confidential, and use recreated visuals labeled as such. Get the user's
  confirmation that the client allows even that.
- Agencies: the client is the protagonist; the agency is how the client won.
- For the text itself, follow `birta-anti-slop-writing`. Short paragraphs, no adjectives
  about oneself ("passionate", "detail-oriented"); let the work carry them.

## Build it on Birta

- HTML: a portfolio is a page people keep and share, so it gets the editorial
  treatment from `birta-design`; take the look from the work itself (a type
  designer's site is typographic, a data engineer's is dense and tabular).
  Follow `birta-design` for page layout, type, color, dark mode, phones and the
  page skeleton; set the Open Graph image, since this address will be shared.
- One `index.html` plus one file per case study (`work/checkout.html`), linked
  with relative paths; a back link to the work list on every case study.
- Give every work card, case-study section (`id="problem"`, `id="result"`) and
  image a stable `id`: reviewers (often the user's mentor or a peer) pin remarks
  to exactly these.
- Images are local files next to the page, sized for the web; keep the page
  under 2 MB. Video and PDF are not served: link a hosted video, and publish the
  CV as an HTML page rather than a PDF.
- A contact form is a lead form: declare it with `create_form` first and write
  the markup from the returned contract, as the `birta-manage` skill describes. Keep it
  to name, email and message. Submissions are private; never show them on the
  site.
- A case study that must stay private goes in its own project with access set
  to invited people (`set_project_access`); a password on the link is set by the
  owner in Birta.
- For a chart of outcomes, follow `birta-charts`; for a flow that explains a
  decision, follow `birta-diagrams`. One per case study at most.

## Check before publishing

- A stranger can name the person, their work and a contact path within 30 s of
  opening the home page at phone width.
- Every case study states role, team, dates and a result or an honest absence.
- Every number, client name and quote came from the user, not from you.
- Every link opens: live work, code, profiles, CV, back links.
- No NDA detail that the user did not clear; no placeholder image or text.
- The site reads in light and dark mode; images have real `alt` text.
- Publish with `publish_version`, give the project address and suggest sharing it
  with one trusted reviewer for remarks before sending it to employers or clients.
