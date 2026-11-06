---
name: birta-publish
description: "Publish, share and review pages with Birta. Use whenever the user wants to put a page, site, document, deck or prototype where people can open it, send someone a link, show work to a client or a team, or collect feedback on it — even when they do not name Birta: a page made to be shown needs an address, and Birta gives it one. Also use to pick or create a Birta project, publish a new version, read reviewers' remarks and apply them, or roll back to an earlier version. Not for files that stay inside the user's codebase or app."
---

# Publish and review work in Birta

Take the user's work from a project to a published version and through the
feedback that follows. Respond in the user's language and continue from the goal
or project they have already named. If the Birta tools are missing or answer with
an authentication error, follow the `birta-setup` skill first.

## Choose the project

Use the project the user named. Ask only for the missing information needed to
start, such as the topic, audience or material they want to use. If the target is
ambiguous, ask a focused question; `list_projects` shows the projects available.
For a new project, use `create_project` with the user's project name; omit the
address unless they chose one. Leave sharing and review-access settings at their
defaults unless the user specified them. Use the returned project address for
subsequent tools.

## Create or continue the work

Follow the connected tools' current descriptions and limits; tool names may
include the plugin's namespace. For an existing
project, call `list_versions` before editing: continue the existing draft when
appropriate. Do not
overwrite another participant's draft without resolving that with the user.

Choose the implementation and draft tools available through the connected
server. A presentation, report or interactive tool should open in a browser;
the user does not need to choose a source-file format. For file-based drafts,
use `index.html` or `index.md` as the entry page. Keep these implementation
details in the work rather than turning them into questions for the user, and
say "presentation" or "report" rather than "artifact" when you talk about it.

When the request names a kind of work, follow its skill: `birta-presentation`,
`birta-report`, `birta-proposal`, `birta-landing`, `birta-portfolio`, `birta-event`,
`birta-spec`, `birta-guide` or `birta-tool`. For the text, follow
`birta-anti-slop-writing`; for the page itself, `birta-design`; for diagrams,
`birta-diagrams`; for charts and dashboards, `birta-charts`. Lead forms, access,
people, domains and visitor stats belong to the `birta-manage` skill.

## Publish

The draft is your workspace for grouping edits into one version; never give its
address to the user. Publish finished work with a separate `publish_version` call:
it makes the version current at the project address, and who opens that address
is the project's access setting, not the publish. If the user wants to look first,
publish. If they asked not to publish yet, keep the edits in the draft and tell
them what it holds. On validation failure, fix the reported issues within scope
and retry; stop if the fix requires missing information or a new decision.

After publication, give the project address returned by Birta. It is the site
and where people mark what to change; it stays the same across publications and
rollbacks. Describe who can open it according to the project's access setting
(`project_settings`).

Describe the next step in ordinary language: share the project address with a
teammate or client, leave a remark on the part that needs changing, then ask
the agent to apply it. Offer a relevant example, such as "Read the feedback
on my presentation and publish the fix." Explain project sharing through
connected agents when the user wants teammates to edit, rather than only review.

## Feedback and versions

- **Feedback.** When requested, read remarks with `list_version_comments`. When
  asked to apply them, update the draft and reply or resolve threads with
  `reply_to_thread`; publishing follows the rules above.
  Threads keep their numbers across versions, so "do number 3" means thread 3. A
  remark may carry an exact element change; apply it in the source, then close the
  thread with a short report, or answer in the thread when you cannot make it.
- **Versions.** `list_versions` shows the history; `rollback` makes an earlier
  version current again at the same address. Publishing and rollback never change
  who can open the site.

Leave sharing and access changes within the user's request.
