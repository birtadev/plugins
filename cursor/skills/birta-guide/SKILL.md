---
name: birta-guide
description: "Write a page people consult or work through rather than read once — a how-to guide, a product manual or knowledge base, a lesson or course step, an FAQ, a restaurant menu, a price list, a catalog or collection — picking the kind from what the reader is trying to do, and publish it to Birta so readers open it by link and leave remarks where the text failed them. Use whenever the user asks for a guide, instructions, a manual, documentation for people, a handbook, an FAQ, a tutorial, a lesson, a menu, a price list, a catalog or a collection, whether or not they say where to host it. Not for a README or docs that live in the codebase."
---

# Guides, manuals, lessons, menus and catalogs on Birta

The reader arrives with a job: do this, learn this, look this up, choose one of these.
The page succeeds when they find the right entry in seconds and can stop reading as
soon as the job is done. Everything else is in the way.

## Ask before you build

Skip any question the user has already answered.

1. Who reads it and what do they already know? A beginner needs one path and
   expected results; a practitioner needs the steps and nothing else.
2. What must the reader be able to do or choose when they close the page?
3. Where does the content come from: the user's material, a product you can
   inspect, or facts you still have to collect? Never invent steps, prices or specs.
4. For a menu or catalog: how many items, what groups, what each item must show
   (price, size, allergens, availability) and whether people can order or inquire.

## Pick the kind, then its structure

One page serves one kind. Mixing teaching into a how-to, or steps into a reference,
is the most common failure. A manual or knowledge base is several pages, one per kind.

| Reader wants to | Kind | Shape |
| --- | --- | --- |
| Get one task done | How-to guide | Goal in the title, steps, done state |
| Learn by doing | Lesson or tutorial | One path, visible result after each step |
| Look something up | Reference or manual | Mirrors the product, same entry shape |
| Choose from options | Menu or catalog | Groups, scannable entries, a price or spec |

**How-to guide.** Title names the task ("Connect your own domain"). Open with who
it is for, what they need first, and how long it takes. Steps in order, one action
each, with the visible result where it is not obvious. Fork with "If …, then …"
rather than a separate section. End with how to confirm it worked and what to do
when it did not. Link to background instead of explaining it.

**Lesson or tutorial.** Say at the top what the learner will have built or done.
Small steps, each producing something they can see, with the expected output shown.
Warn before a step that surprises. Add a short check after each block: a question,
a thing to try, or a result to compare, with the answer folded in `<details>`. Close
with what they accomplished and the next lesson. One path, no options.

**Reference, manual, knowledge base.** Organize by the product's own structure, not
by what seems interesting. Every entry has the same parts in the same order (what
it is, settings, limits, errors, example). State facts, do not persuade. A short
answers section (FAQ) goes under the topic it belongs to, not in one long list.

**Menu or catalog.** Groups in the order people decide (starters before mains;
categories before variants). About seven entries per group; split a bigger one.
Each entry: name, a one-line description in concrete words (ingredients, material,
size), the price or key spec in the same type as the text, and marks for what
matters to the choice (vegan, gluten, in stock, new). Combine variants into one
entry. Put the item the owner wants noticed first or last in its group.

## Craft rules

- Headings are the reader's tasks or the product's parts, in their words, not
  yours. The table of contents must read as a list of jobs.
- Top of the page: scope, audience and prerequisites in three lines, then the
  content. History, rationale and credits go to the end or another page.
- Numbered lists for sequence, bullets for sets, tables for anything with the
  same fields repeated. Never a numbered list of things that are not steps.
- Show the exact thing: the command, the field label, the expected message, the
  real price. Screenshots only where words fail, and never as the only carrier.
- Progressive disclosure: the common case in the open, edge cases and long
  output folded in `<details>`, deep material on its own page.
- Omit steps any competent reader does unprompted; keep the judgement calls.
- Do not pad: no "in this section we will", no restating the heading, no
  motivation paragraphs. For the text itself, follow `birta-anti-slop-writing`.

## Build it on Birta

- Markdown (`index.md`) for guides, lessons, references and knowledge bases: it
  renders headings with anchors, tables, `<details>` and Mermaid. One file per
  page, linked by relative links; an `index.md` that lists the pages is the TOC.
- HTML (`index.html`) for a menu or catalog, where grouping, columns and marks
  need layout, and for any page with a form. Build the entries as static HTML
  with one `id` per group and per item; filters may hide and show, never render.
- For page layout and type, follow `birta-design`. For charts, follow
  `birta-charts`. For diagrams, follow `birta-diagrams`.
- In HTML, give every heading, step, entry and check a stable `id` (`step-3`,
  `dish-ramen`) so remarks stay attached across versions; keep ids when you
  rewrite. In Markdown, remarks address blocks by position: keep heading wording
  and block order stable, and add new material at the end of a section.
- A catalog or menu with "order", "inquire" or "book" needs a lead form:
  declare it with `create_form` and write the markup from the contract it
  returns, as the `birta-manage` skill describes.
- A lesson series or manual is one project; a new version at the same address
  is how it grows. Do not start a project per page.

## Check before publishing

- Each page is one kind; its title says the task, the lesson's outcome, the
  entry or the group.
- Every step has one action and, where needed, its visible result; the guide ends
  with a way to confirm success.
- Every price, spec, command and label comes from the user's material or the
  product itself; nothing is a placeholder.
- The TOC reads as jobs; a reader can land on any section from a link and know
  where they are.
- Entries in a group share the same fields; marks and prices line up.
- Phone width and dark mode read cleanly; folded details open; ids are unique.
