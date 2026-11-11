# Birta for Codex and ChatGPT

[Website](https://birta.dev) · [Install](#install) · [Skills](#skills) · [Issues](https://github.com/birtadev/plugins/issues)

![Claude Code plugin](https://img.shields.io/badge/Claude_Code-plugin-1E7C71)
![Codex plugin](https://img.shields.io/badge/Codex-plugin-1E7C71)
![Hermes Agent plugin](https://img.shields.io/badge/Hermes_Agent-plugin-1E7C71)
[![MIT license](https://img.shields.io/badge/license-MIT-1E7C71)](https://github.com/birtadev/plugins/blob/main/LICENSE)

## Why Birta

Agents now make a lot of our work: sites, reports, documents, decks. That work should
not be locked into the agent or the provider that made it. Birta keeps it in one place:

- **Any agent, same artifacts.** Claude Code, Codex, ChatGPT, Hermes or Birta's own
  agent can pick up the same project. Switch agents without moving your work.
- **Teammates on different agents.** Everyone on a project brings the agent they like,
  reviews on the same page, and any agent can apply the feedback.
- **Free forever for personal use.** Your artifacts stay free to publish and share.

[Birta](https://birta.dev) is a shared workspace where people and agents turn drafts
into finished work. Publish a site, report or document, review it together on the page,
and ask your agent to apply the feedback.

Birta connects to your agent through its MCP server (`https://birta.dev/mcp`) and adds
the skills below. You sign in to Birta in the browser; nothing here holds keys or tokens.
Every tool call goes to `birta.dev` and acts on the Birta projects you can access:
files, versions, publishing, sharing, lead forms and domains.

## Install

### Codex

```bash
codex plugin marketplace add birtadev/plugins
codex plugin add birta@birta
```

Then sign in to Birta in the browser with `codex mcp login birta`.

### ChatGPT

Find Birta in the Plugins directory and connect it; ChatGPT opens the Birta sign-in.

### Receive mentions

Call your agent into a Birta review thread with `@chatgpt` or `@codex`. In ChatGPT, ask
it to receive your Birta mentions and confirm: each mention then reaches it at once.
Codex picks its mentions up when you ask it to work through your remarks.

## Skills

Skills for a task: say what you want to make and the agent follows the matching one.

- [`birta-presentation`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-presentation/SKILL.md): A deck that opens in the browser and moves at the viewer's pace: one idea per slide, titles that state the point, notes for the speaker. _Try: "Make a pitch deck for my course"_
- [`birta-report`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-report/SKILL.md): A report or update that leads with the conclusion: the numbers, what they mean and what to do next, with charts drawn to scale. _Try: "Turn these Q3 numbers into a report"_
- [`birta-proposal`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-proposal/SKILL.md): A client proposal: the client's problem, the scope, timeline and price, assumptions, and one next step they can take on the page. _Try: "Write a proposal for the website redesign"_
- [`birta-landing`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-landing/SKILL.md): A landing, service, launch or waitlist page: one offer, proof, one call to action and a lead form that sends submissions to you. _Try: "Make a landing page for my bakery"_
- [`birta-portfolio`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-portfolio/SKILL.md): A portfolio or case-study site that shows the thinking behind the work: problem, approach, result, and a way to get in touch. _Try: "Build my portfolio from these three projects"_
- [`birta-event`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-event/SKILL.md): An event page with the date, program and place above the fold, and registration that puts people on the guest list. _Try: "Make a page for our Saturday bike ride"_
- [`birta-spec`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-spec/SKILL.md): A PRD, RFC or design doc in Markdown: problem, goals and non-goals, the decision, alternatives, open questions, with diagrams. _Try: "Draft a PRD for the new onboarding"_
- [`birta-guide`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-guide/SKILL.md): A guide, manual, lesson, menu or catalog people can work through or browse: task-based sections, steps with results, navigation. _Try: "Write a setup guide for our API"_
- [`birta-tool`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-tool/SKILL.md): A calculator, quiz, small game or demo that runs in the browser: sensible defaults, instant results, shareable state. _Try: "Make a pricing calculator"_

Base skills, used by the task skills and on their own:

- [`birta-setup`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-setup/SKILL.md): Checks the Birta connection, helps you sign in, and asks what you want to make first. _Try: "Set up Birta"_
- [`birta-publish`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-publish/SKILL.md): Picks or creates a project, publishes your work at its address, reads the feedback left on the page, applies it and publishes the next version. _Try: "Publish this page so my client can review it"_
- [`birta-manage`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-manage/SKILL.md): Project settings: who can open it, invited people, lead forms and their submissions, your own domain, visitor stats. _Try: "Connect my domain to this site"_
- [`birta-anti-slop-writing`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-anti-slop-writing/SKILL.md): Text that reads as if a person wrote it for a specific reader: concrete, front-loaded, free of the patterns that mark generic model prose. _Try: "Rewrite this page so it sounds like us"_
- [`birta-design`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-design/SKILL.md): Designs the page itself: format, typography, color, dark mode and phone layout, with ids that keep reviewers' remarks attached from version to version. _Try: "Make this page look deliberate"_
- [`birta-diagrams`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-diagrams/SKILL.md): Draws flows, architectures, timelines and org charts that show the real mechanism, with Mermaid in documents or SVG in pages. _Try: "Add a diagram of our onboarding flow"_
- [`birta-charts`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-charts/SKILL.md): Builds charts, KPI tiles and dashboards from real numbers, drawn to scale and readable in both themes. _Try: "Add a chart of signups by month"_
- [`birta-binary-files`](https://github.com/birtadev/plugins/blob/main/codex/skills/birta-binary-files/SKILL.md): Puts images, fonts and other binary files into a draft: one HTTP send to an upload address, or base64 text when the agent has no network. _Try: "Add these three photos to the gallery"_

The agent picks a skill up on its own when your request matches it.

## Get started

Ask your agent to set up Birta, or say what you want to make:
"Create a presentation card about me and publish it in Birta so I can share it."

## Support

Questions and bug reports: [open an issue](https://github.com/birtadev/plugins/issues)
or visit [birta.dev](https://birta.dev).

## License

[MIT](https://github.com/birtadev/plugins/blob/main/LICENSE)
