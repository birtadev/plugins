---
name: birta-landing
description: "Build a landing page — a service page for a freelancer or small business, a lead-generation page, a waitlist or coming-soon page, a product or course launch page — with one offer, real proof, one call to action and a lead form that delivers to the owner, and publish it to Birta so it has an address to share and a page to review on. Use whenever the user wants a page that sells one thing or collects sign-ups — a landing, service, waitlist, coming-soon, launch or lead page — whether or not they say where to host it: a landing page exists to be shown, and Birta gives it an address. Not for pages inside the user's own app or codebase."
---

# A landing page on Birta

A landing page has one job: a visitor who arrives with a question ("is this for me,
what do I get, what does it cost, what do I do next") answers it in seconds and takes
one action. Everything on the page serves that action or is cut. The page is also
where the owner and their reviewers will mark what to change, so build it so remarks
survive each new version.

## Ask before you build

Ask only what the user has not said. Each answer changes the page.

1. **The one action.** Submit a form, book a call, join a waitlist, buy, write an
   email? What should happen after: who replies, how fast, what the visitor gets.
2. **Who arrives and from where.** An ad, a post, a profile link, a cold link, a
   referral. The headline must match what they clicked and the words they use.
3. **What proof exists.** Real names, numbers, logos, past work, reviews, a credential.
   Nothing is invented; if there is none yet, the owner's own story is the proof.
4. **The price, or why it is not shown.** A fixed price, "from" price, packages, or a
   quote after a call; a waitlist or launch page needs a date or "what you get first".

## Outline

Top to bottom. Drop a section only when the variant has nothing real to put in it.

| Section | It must contain |
| --- | --- |
| Hero | Outcome for whom in one line, one sentence of how, the single button |
| Proof strip | 1–3 specific items near the headline: a number, a name, a logo |
| Who it is for | The visitor's situation in their words; who it is not for |
| The offer | What they get, concretely: deliverables, scope, format, timing |
| How it works | 3–4 steps from clicking the button to the result |
| Pricing | The price or "from", what each option includes, one marked as the usual pick |
| Objections | 3–5 real doubts answered: price, fit, time, risk, "what if" |
| Final call | The offer restated in one line, the same button, the form |

By variant:

- **Service page**: what you do, what it costs, how to get in touch. Past work with
  a result each; the form asks for the project, not a résumé.
- **Lead generation**: the offer is the thing they receive (a quote, an audit, a
  guide); say what arrives, when and from whom.
- **Waitlist / coming soon**: hero, proof or founder note, what early members get,
  form with email only, what happens after joining. No pricing table.
- **Launch**: what ships and when, what is inside, price and any launch terms,
  then the objections section carries the most weight.

## Craft rules

- One headline, under about ten words, that names the result for the audience, not
  the product's category. The subline says how, with one specific.
- One call to action on the whole page. Repeat the same button with the same label;
  never add a second competing action, a menu to other pages or outbound links
  above the fold. The label says what happens: "Get a quote by Friday", not "Submit".
- Under the button, one line that removes the friction: reply time, no payment now,
  what you will not do with the address.
- Proof is specific or absent: a full name with role, a number with its period, a
  logo of a real client. No stock faces, no invented reviews, no round-sounding
  "thousands". With no customers yet, a short honest note from the owner beats
  silence.
- Show the price when the owner has one. "From X" works when scope varies; two or
  three packages with the usual pick marked beat a long comparison. Hidden prices
  send the visitor away to find them.
- Objections come from the owner's real conversations, not a generic FAQ. One doubt,
  one plain answer, including who the offer is not for.
- Write the copy before the layout, in the visitor's words. Frameworks (problem,
  consequence, solution; attention, interest, desire, action) are a check on the
  order, not a template to fill. For the text itself, follow `birta-anti-slop-writing`.
- Keep it as short as the decision allows: a waitlist fits on two screens, a service
  page on five. Every extra section must answer a real question.

## Build it on Birta

- The page is HTML (`index.html`): it carries a form, and Markdown drops forms. For
  page layout, type, color, dark mode and phone widths, follow `birta-design`; it
  decides the treatment, so bring the subject's own materials, not a template look.
- Declare the lead form first with `create_form` (form key, field keys, types,
  choice values), then write the markup exactly from the intake contract it returns,
  as the `birta-manage` skill describes. Ask for the minimum: email, plus one field that
  tells the owner what the visitor wants. Every added field costs sign-ups.
- Give each section a stable `id` (`hero`, `proof`, `offer`, `steps`, `pricing`,
  `faq`, `cta`) and the form its own, so reviewers' remarks follow the block across
  versions. Keep the readable content in static HTML.
- A "how it works" that is a real sequence may be a diagram; follow `birta-diagrams`.
  Numbers worth a chart are rare here; if there are any, follow `birta-charts`.
- Title, description and Open Graph tags matter more than usual: the address will
  be pasted into ads, posts and messages. Per `birta-design`, set them all.
- Publish with `publish_version`, give the owner the project address, and remind
  them that who can open it is the project's access setting. Submissions arrive
  through `list_leads`; they stay private to the owner.

## Check before publishing

- The headline and the button are readable without scrolling at 360px, and a
  stranger can say in five seconds what is offered, for whom, and what to do.
- Exactly one action on the page; every button carries the same label.
- Every proof item is real and specific; every price is the owner's; every FAQ
  answer is one the owner would give in person.
- The form matches the `create_form` contract field for field, and the page says
  what happens after submitting.
- Sections and the form have stable ids; nothing links away from the page except
  what the owner asked for; light and dark mode both read.
