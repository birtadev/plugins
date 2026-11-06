---
name: birta-event
description: "Build an event page — a meetup, workshop, webinar, conference, community ride, wedding or party invitation — that tells a guest in one screen what it is, when and where, whether it is for them, and gets them onto the guest list through a registration or RSVP form the organizer reads; publish it to Birta so the invitation is a link. Use whenever the user asks for an event page, an invitation, a registration or RSVP page, a page for a talk or workshop, or a \"save the date\", whether or not they say where to host it."
---

# Event page on Birta

The page has one job: turn a person who opens the link into a confirmed guest who
shows up. Everything else serves that: the first screen answers what, when, where
and for whom; the rest removes doubts; the form is the only exit. After the event
the same address can hold the recording or the thanks, so build it to be revised.

## Ask before you build

Ask only what the user has not said, in one message:

1. The facts: name, date, start and end time with the time zone, venue with a
   street address or the online platform, who hosts it. Do not invent any of them;
   a missing fact stays out of the page, and the owner hears which ones are
   missing before the page is shared.
2. Who the guest is and what they get: a skill, a decision, a night out, a seat
   at the table. Also who the page is not for, if that matters.
3. What a sign-up must collect beyond name and email (dietary needs, plus-one,
   ticket type, company), and whether seats, a deadline or a price are real.
4. For private occasions (wedding, party): is the page for invited guests only?
   That is the owner's access setting, so ask, do not assume.

## What the page holds

- **Lead (first screen).** Name, one line on what a guest gets, date and time
  with zone, city and venue or "online", the main button.
- **Why come.** Three to five concrete outcomes, or the occasion in the host's words.
- **Programme.** Times, titles, who speaks; one line per item on why it matters.
- **People.** Speakers or hosts with a role and the one fact that makes them credible.
- **Place.** Address, how to get there, parking or transit, a map link; for online,
  the platform and when the join link arrives.
- **Practical.** Price, seats, deadline, language, dress code, accessibility,
  children, what to bring.
- **Sign up.** The form, the same button text as the lead, what happens after sending.
- **Contact.** One person or address for questions.

Drop a part that has nothing real behind it rather than filling it. A wedding or
party invitation keeps lead, place, practical, RSVP and contact, in the hosts'
voice; it does not need outcomes or speakers.

## Craft rules

- The first screen reads in a few seconds without scrolling on a phone. Put the
  date and the place in text, never only in an image.
- Write dates and times in full with the zone (`Thu 12 Mar 2026, 18:30–21:00
  CET`); for online events add one other zone the audience lives in. Add an
  add-to-calendar link (a calendar URL; Birta does not serve `.ics` files).
- Repeat the main button after the program and at the end; every copy leads to
  the same form. One button text throughout, in the guest's words
  ("Save my seat", "RSVP by 1 May"), not "Submit".
- Say what happens after signing up: confirmation, when the join link or ticket
  comes, whether a seat is guaranteed or a waitlist exists.
- Deadlines, seat counts and prices appear only when they are true, with the date
  or number. No countdown theatre, no invented scarcity.
- Group a long program by day or track; keep the whole thing readable without a
  click. Mark breaks and the start and end, so a guest can plan travel.
- Social proof is a past edition, a photo, or a named person; not adjectives.
- Keep private things off the page: guest lists, the hosts' life story, events
  only some guests are invited to.
- Ask the form for the least it needs; explain any field that is not obvious.
- Plan the page's next life: after the event, swap the form for the recording,
  the photos or the thanks, and keep the address.

For the text itself, follow `birta-anti-slop-writing`. For page layout, type and color,
follow `birta-design`. For a venue plan or a route sketch, follow
`birta-diagrams`. If the page shows numbers from past editions, follow
`birta-charts`.

## Build it on Birta

- The page is HTML (`index.html`): it carries a form, and `birta-design` says a
  Markdown page drops forms. Treat it as a page people keep: one bold idea drawn
  from the occasion itself, the rest calm.
- Declare the form first with `create_form`: a form key, field keys, types and
  choice values for every question agreed above. Write the markup exactly from
  the intake contract it returns; add nothing it did not declare. Submissions are
  private: report them to the owner on request (`list_leads`, `get_lead`), never
  on the page or in a thread.
- Give every part a stable id (`id="lead"`, `id="program"`, `id="talk-3"`,
  `id="venue"`, `id="rsvp"`), so a reviewer's remark on a session or a speaker
  survives the next version. Change a slot by editing it in place.
- Keep the program, the facts and the form in static HTML. Scripts may handle
  the calendar link or navigation, never the content.
- Set a title, meta description and Open Graph tags that name the event with its
  date: the link will be pasted into chats and invitations.
- Access is the owner's decision. Describe who can open the address from
  `project_settings`; change it with `set_project_access` only when the owner
  asked, for example invited guests only for a wedding.

## Check before publishing

- Phone width: the first screen shows what, when, where, for whom, and the button.
- Every date has a zone; every address has a map link; no invented fact and no
  placeholder text on the page.
- The form markup matches the declared contract field for field, and the page
  tells the guest what happens next.
- Deadline, price and seat count match what the user said, or are absent.
- Ids on every section, speaker and program item; the page reads in dark mode.
- Project and draft work as the `birta-publish` skill describes, access as
  `birta-manage` does. Publish with
  `publish_version`, hand over the project address, and say who can open it and
  where the sign-ups will arrive.
