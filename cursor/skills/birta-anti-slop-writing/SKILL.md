---
name: birta-anti-slop-writing
description: "Write the text of a page people will read — landing copy, report prose, a proposal, a spec, slide text, a guide — so it reads as if a competent person wrote it for one specific reader, with real facts and a clear point, instead of generic generated prose. Use whenever you write or rewrite more than a label on a page that will be published or shown to people, and before publishing any page whose words matter."
---

# Write the text of a Birta page

A page in Birta is read by a real person who came for one thing: a decision, a
number, a way to do something. The text succeeds when that person gets it fast
and believes it. Generated prose fails this in a predictable way: it is written
for nobody in particular, so it says things that are true of everything and
specific to nothing. The fix is not a banned-word list. It is knowing who reads,
what they must take away, and what you actually know.

## Before you write

- **Know the reader.** Name one person: a buyer comparing tools, a manager who
  decides on Friday, a developer setting it up. Write for them and let others
  overhear. If you cannot name the reader, ask the user.
- **Know the one thing.** Write the single sentence the reader must take away.
  If the page is a proposal, that sentence is the proposal. If it is a report, it
  is the finding. Everything else exists to support or qualify that sentence.
- **Know the material.** Gather what you have: the user's words, files, numbers,
  the product itself, cited sources. Write only from that. Never invent facts,
  numbers, quotes, customers, testimonials, dates or statistics. Where a figure
  is missing, say so or ask; where it is an estimate, label it as one.
- **Know the stakes.** What the reader loses by misreading sets length and order.

## Write it

- Say the specific thing. "Deploy takes 40 seconds" beats "fast deployment".
  "Three of the five pilots churned at month two" beats "retention challenges".
- Lead with the point, then the reason, then the detail. Do not build up to it.
- Use the shortest common word that is exact: use, not utilize; help, not
  facilitate; show, not showcase; is, not serves as.
- Prefer verbs to nominalizations: "we decided" not "a decision was made".
  Name who acts; passive voice is fine only when the actor is unknown or
  irrelevant.
- Cut every word that carries nothing. Read each sentence and ask what it gives
  the reader; if nothing, delete it. Read the paragraph and ask the same.
- Keep the reader's units, terms and conventions; do not explain what they know.
- One idea per sentence, one topic per paragraph. Vary sentence length because
  the ideas vary, not to a rhythm.
- Let the tone follow the genre and the user's own words. A spec is plain and
  exact; landing copy is confident and concrete; a guide talks the reader
  through each step in second person. Nothing on a Birta page is "artifact" or
  "content": say website, report, proposal, deck.
- Say what you believe with the certainty you have. Hedge once, where the doubt
  really is, in a concrete way ("based on two weeks of data"), not everywhere.
- Say it the way you would say it aloud to the reader across a table. If a
  sentence would sound strange spoken, rewrite it.

## Sentences and words

Rules after ASD-STE100, the controlled language written for maintenance manuals,
where a sentence misread costs more than a sentence reread. They hold in any
language. Apply the numbers to a spec, a guide, a report or a proposal; landing
copy and slide text keep the spirit and set their own rhythm.

- An instruction is at most 20 words; a descriptive sentence at most 25. A
  paragraph covers one topic in at most six sentences.
- One word for one thing across the whole page: once it is an "order", it is
  never later a "request" or a "ticket". One meaning per word: do not use a word
  in two senses.
- A term the reader knows needs no gloss. A new term is explained once, at its
  first use, and then used unchanged.
- No chain of more than three nouns: "service timeout config" is the limit.
- Simple tenses: present, past, future. No stacked participles or clauses the
  reader has to unwind.
- A condition with several parts, or a sequence, is a list, not a sentence.
- Instructions are imperative, one action per step: "Open the file." Two actions
  in one step only when they happen at the same time.
- A warning starts with the plain command, then names the harm: "Do not drop
  the table. The data is gone for good."

To explain something, keep this order: first sentence says what it is or what
the answer is; then why it matters; then how it works, in steps or on one
example; limits and risks last, when there are any. One concrete example beats
two abstract paragraphs.

## Patterns to cut

Each pattern is a symptom of not having a specific thing to say. Patching the
symptom alone produces a new, equally recognizable voice; find what you meant.

| Pattern | Hides | Write instead |
| --- | --- | --- |
| "In today's fast-paced world" openers | No point yet | The point |
| "It's not X, it's Y"; "not just X but Y" | A staged claim | The claim about Y |
| Triads: "fast, simple, secure" | Padding | The one or two that matter |
| delve, tapestry, landscape, leverage, robust | Abstract praise | The concrete property |
| seamless, pivotal, crucial, vibrant | Abstract praise | A number or an example |
| serves as, stands as, boasts, features | Avoiding "is", "has" | is, has |
| "a testament to", "underscores", "turning point" | Inflation | What changed |
| Trailing "-ing": "…, ensuring reliability" | Unproven effect | Evidence, or nothing |
| "Experts agree", "studies show", "many users" | No source | The named source, or cut |
| "Great question", "Let's dive in" | Chat leftovers | Nothing |
| "In summary", "In conclusion", "Overall" | A recap | The last fact or next step |
| very, truly, incredibly, deeply, genuinely | A weak claim | The claim with a number |
| "may potentially", "it's important to note" | Fear of error | One qualifier, placed |
| Em dashes as the connector everywhere | Unsorted thoughts | A full stop; two sentences |
| Bold on half the nouns; emoji bullets | Format as thought | Plain text; bold once |
| "Challenges and outlook" sections | Nothing concrete | The specific risk and the plan |
| Heading restated as first sentence | Filling space | New information |

Rule of three, dashes and qualifiers are tools, not faults. Keep three items when
there are three. Keep a dash when it does what a dash does. Keep the qualifier
the data supports. Do not overcorrect into slang, fragments, staged candor or
invented anecdotes to sound human; that is just a different template.

## Structure

- Front-load. Title, first paragraph and each section opener carry the point, so
  someone who reads only those knows the answer.
- Headings are sentence case and say what the section tells, not its category:
  "Churn fell after onboarding changed", not "Results". Avoid "X and Y" headings,
  unless the section really covers two things, like "Price and terms".
- Paragraphs of two to five sentences on screen. A one-sentence paragraph is for
  a point that must stand alone, not for drama.
- Use a list only for things that are a list: steps, options, requirements. Use
  prose for reasoning, since a list hides how points connect. Keep list items
  parallel and about the same length; no bolded label followed by a colon on
  every item.
- Use a table when the reader will compare rows. Keep cells short.
- Match length to stakes. A landing page has a few hundred words; a spec has as
  many as the behavior needs; a slide has one claim and its support.
- A proposal or report ends with the decision asked for or the next step, with
  an owner and a date when you know them.

## Review your draft

Run through this before publishing, reading the page as the named reader.

- [ ] The one thing is in the title or first paragraph, in the reader's words.
- [ ] Every number, name, quote and date traces to the user's material or a
  source on the page. Nothing was invented to fill a gap.
- [ ] Each paragraph says something only this page could say. Delete any that
  would fit on any competitor's page unchanged.
- [ ] No sentence from the pattern table survives, and none was replaced by a
  new mannerism.
- [ ] Opening and closing are information, not throat-clearing or a recap.
- [ ] Outside landing copy and slide text, no sentence runs past 25 words and no
  paragraph past six sentences; no term changes its name halfway down the page.
- [ ] Headings read as a summary on their own.
- [ ] Lists hold list-shaped things; reasoning is prose.
- [ ] Read aloud once; every sentence sounds like a person speaking to the reader.
- [ ] The page is in the user's language and the reader's register; terms match
  what the product and the user actually call things.

For layout and type, follow `birta-design`; for diagrams, `birta-diagrams`; for
charts, `birta-charts`.
