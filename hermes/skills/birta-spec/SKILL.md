---
name: birta-spec
description: "Write a PRD, RFC, design doc or technical spec — the problem and its boundaries, the proposed answer, the alternatives weighed, the measures of success and the questions still open — and publish it to Birta as a Markdown page teammates open by link and review block by block, so a team can decide and build from it. Use whenever the user asks for a PRD, product spec, one-pager, RFC, RFD, design doc, technical design, architecture proposal or decision record, or wants a plan reviewed by other people, whether or not they say where to put it. Not for a spec the user keeps in a repository, unless they want people to review it by link."
---

# Specs on Birta

A spec exists so people who were not in the room can decide: is this the right
problem, is this the right answer, what would change their mind. Reviewers leave
remarks on its blocks and the next version answers them at the same address.
Write for that reader, not for the author. Three kinds; name the page's kind in
the title and the front matter:

| Kind | Answers | Owner |
| --- | --- | --- |
| PRD | What problem, for whom, what done looks like | Product |
| RFC | A proposal that wants objections before it is built | Engineering |
| Design doc | How a chosen thing will be built, and why this way | Engineering |

## Ask before you build

Ask only what the conversation has not answered, in one message:

1. Which kind, and what decision the reader is asked to make (approve, choose
   between options, or only comment).
2. The problem in the user's own words, and the evidence behind it: a metric,
   support tickets, an incident, research. Without evidence, write "assumed".
3. What is out of scope, and what the user already ruled out and why.
4. Who reviews, and by when a decision is needed.

Do not ask about anything the user already told you, and do not invent what
they did not: constraints, numbers, stack, dates. An unknown is an open question
in the page, not a guess in a sentence.

## Outline

Every kind opens with a header the reader scans in ten seconds: kind, status
(draft, in review, decided, abandoned), owner, reviewers, decision deadline, and a
summary of three sentences: problem, proposal, what is asked of the reader. In
Markdown this is the front matter plus the first paragraph.

| Part | Must contain | PRD | RFC / design doc |
| --- | --- | --- | --- |
| Problem and context | Who hurts, how often, what it costs; what exists | yes | yes |
| Goals and non-goals | Outcomes to reach; plausible things left out | yes | yes |
| Users and scenarios | Named roles and the situations they meet | yes | if user-facing |
| Requirements | Numbered, each testable, each tied to a goal | yes | — |
| Proposal | The design in one overview, then the parts | sketch only | yes |
| Alternatives | Each real option, its trade-off, why not | brief | yes |
| Cross-cutting | Security, privacy, data, operations, cost | if relevant | yes |
| Rollout and risks | Phases, what can go wrong, how it is undone | brief | yes |
| Success metrics | Baseline, target, when measured, where read | yes | yes |
| Open questions | Each with an owner and the options on the table | yes | yes |

Drop a part that has nothing in it rather than filling it; say in one line why
it is absent if a reader would look for it.

## Craft rules

- Lead with the problem, solution-free. A reader should be able to agree with the
  problem and still reject the proposal.
- A requirement is a sentence someone can check: "a draft saves within 2 s on a
  3G phone", never "fast", "intuitive" or "scalable". Number requirements and
  decisions so remarks can name them.
- A metric has a baseline, a target, a date and a place to read it. A metric with
  no baseline is a wish; mark it as one.
- Alternatives are the options you nearly chose, with the reason they lost. One
  straw man next to the winner is not an alternatives section. If there was no
  real choice, say so and skip the section.
- Non-goals are things the reader would reasonably expect and will not get.
- Match depth to stakes: a one-page PRD or a three-page design doc is the norm;
  a longer page means two problems that want two pages.
- Keep the page a decision aid, not a build manual: no file paths, no code
  beyond a short sketch of an interface or a novel algorithm. Describe the user's
  path; leave screens to design and modules to engineering.
- Prefer the team's own vocabulary and real names of systems, roles and data.
- For the text itself, follow `birta-anti-slop-writing`.

## Build it on Birta

- Write Markdown (`index.md`), per `birta-design`: the front matter renders as a
  table, so put kind, status, owner, reviewers and deadline there. Headings get
  anchors; keep their wording stable across versions so links keep working.
  Do not convert to HTML for looks.
- Draw the system context, the user's path, a sequence or a state machine as
  Mermaid blocks; follow `birta-diagrams`. A table beats a diagram
  for comparing options.
- Numbers that carry the argument go in a table; a chart only when the shape of
  the data is the point, per `birta-charts`.
- Fold supporting material (query results, long option analyses, interview
  notes) into `<details>` so the main thread stays short.
- Apply remarks by editing the block in place (`edit_file`, `replace_lines`), not
  by regenerating the page. When a remark settles an open question, move it into
  the decisions and close the thread with `reply_to_thread`; update the status in
  the front matter when the decision is made. Keep the earlier reasoning: a
  reader later wants to know what was rejected and why.
- Project and draft work as the `birta-publish` skill describes, access as
  `birta-manage` does. Draft in the
  project draft; publish with `publish_version` and give the user the project
  address. Reviewers' access is the project's setting, not yours.

## Check before publishing

- Kind, status, owner, reviewers and deadline are in the front matter; the
  summary says what the reader must decide.
- Problem is stated without a solution, with evidence or marked "assumed".
- Every requirement is testable and numbered; every metric has a baseline,
  target and date.
- Non-goals and alternatives are real, not padding.
- Nothing in the page came from you rather than the user or a named source.
- Open questions each have an owner.
- Diagrams render, read on a phone and in dark mode, and name real parts.
