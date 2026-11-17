---
name: birta-proposal
description: "Write a client proposal, quote or statement of work for a freelancer or small agency — the client's problem and outcome, bounded scope with exclusions, timeline, price options, terms, a validity date and one next step — and publish it to Birta as a page the client opens by link, reviews with remarks and accepts or questions through a form. Use whenever the user asks for a proposal, quote, estimate, offer, statement of work or SOW, or wants to turn call notes or a brief into something a client can say yes to, whether or not they say where to send it."
---

# A proposal on Birta

A proposal has one reader, the client, and one job: let them say yes without a
second meeting. They must recognize their own problem, see the outcome, pick an
option, know the price and terms, and find a single action at the end. The page
is also where they push back: remarks on a deliverable or a price come back to
you, and the next version answers them at the same address.

## Ask before you build

Ask only what the user has not already said, in one message:

1. What did the client say the problem and the wanted outcome are, in their words?
   Call notes or a brief are enough; the proposal must echo them.
2. One price or options? For each option: the amount, what is in it, and which one
   the user recommends. Fixed price, retainer or hourly with a cap.
3. Dates: when work can start, when each milestone lands, and what the client must
   supply before each one (content, access, approvals).
4. Terms the user actually works by: deposit and payment schedule, revision rounds,
   how changes are priced, how long the offer stands, and what "accept" means
   (a form on the page, an email, a signed contract elsewhere).

Do not ask for a case study, a team page or legal clauses; add them only when the
user supplies them.

## Outline

| Section | Must contain |
| --- | --- |
| Header | Title naming the project, client, provider, date, "valid until" date |
| Your situation | The problem in the client's words and what it costs them |
| Where you want to be | The outcome, measurable where the user has a number |
| What we will do | One paragraph of approach, then numbered deliverables, each bounded |
| Not included | Explicit exclusions; what each would cost if added |
| Assumptions | What the price depends on and what changes if an assumption fails |
| Timeline | Dated milestones, what the client supplies before each |
| Investment | Options side by side, the recommended one marked, what differs |
| Terms | Payment schedule by date, revisions, change requests, validity |
| Why us | One relevant result or project, with a link; two or three sentences |
| Next step | One action and the form or address to do it |

A deliverable is bounded when it says what, how many, in which format and what
"done" looks like. The price is true only for that scope: give exclusions and
assumptions as much space as inclusions.

## Craft rules

- Lead with the client, not the provider. No company history, no mission statement,
  no list of services; the client already chose to read this.
- Keep it short: six to eight sections, readable in ten minutes. Link to the
  portfolio instead of pasting it.
- Price comes after scope and before terms. Never show a number without what it
  buys. Two or three options at most, differing in outcome, not in effort; the
  recommended one marked and priced to be the obvious choice.
- Tie payments to dates or deliverables, not to "completion"; projects rarely end
  on a day anyone can name.
- Mark the offer's end date and say what the client gets by acting before it:
  the start date they wanted, the price as stated.
- End with one action in plain words ("Accept the Standard option", "Book a call
  to discuss"), not "let me know what you think".
- Do not promise results the user did not promise, invent testimonials, or write
  legal boilerplate; the contract is a separate document the user owns.
- For the text itself, follow `birta-anti-slop-writing`.

## Build it on Birta

Follow the `birta-publish` skill for projects, publishing and feedback, and
`birta-manage` for the form and access.

- Build it in HTML: it carries the form, and options need layout. Use the calm,
  working-document treatment from `birta-design`; a proposal is a business page,
  not a landing page. The user's own brand colors and type go first.
- Give every deliverable, option, milestone, term and exclusion its own stable
  `id` (`id="deliverable-3"`, `id="option-standard"`, `id="milestone-2"`), so the
  client's remark on one line stays on that line in the next version.
- Options as equal cards or a comparison table; the recommended one set apart
  once, with borders or fill, not with color on every card. Totals with tabular
  figures and the currency stated.
- A timeline with more than four milestones may be a diagram; follow
  `birta-diagrams`. A chart only for real numbers the client gave, such as the
  cost of the problem; follow `birta-charts`.
- The next step is a lead form: declare it with `create_form` with a choice
  field (accept, discuss) and a choice field for the option, plus name, email and
  a message, then write the markup exactly from the intake contract it returns.
  A submission is a lead the user reads with `list_leads`; tell the user it is an
  acceptance of the offer, not a signed contract. If the user prefers email or a
  signing tool, link to that instead and skip the form.
- Keep the proposal date and version visible; a changed price or scope is a new
  published version at the same address.
- Put the user's materials, logos and fonts in the project files; a proposal must
  not depend on a hotlink that expires before the offer does.

The client reads it in the project at its address; who can open it is the
project's access setting, which the user decides. After publishing, remind the
user to check it and share the address with the client.

## Check before publishing

- Every amount, date and name matches what the user gave; option totals add up.
- Each deliverable is bounded ("a 5-page site in Webflow with the copy you supply",
  not "website design"); exclusions are listed; each assumption names its fallout.
- "Valid until" is a date, payments have dates, and there is exactly one next step.
- The form key and fields match the `create_form` contract, or the chosen
  alternative is linked; no placeholder text or sample figures remain.
- Options, deliverables, milestones and terms carry ids; the page reads at phone
  width and in dark mode; the contact details are the user's own.
