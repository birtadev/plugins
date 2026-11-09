---
name: birta-setup
description: "Connect Birta and take the first step with it. Use when the user asks to set up, connect, sign in to or reconnect Birta, asks what Birta is or what it can do, asks to receive their Birta mentions as they are written, or when the Birta tools are missing or answer with an authentication error. Not for making, publishing or reviewing work: that is birta-publish."
---

# Set up Birta

Help the user reach a useful next step with Birta. Keep the introduction brief,
respond in the user's language, and continue from any goal or project they have
already named. Setup alone does not authorize creating or publishing work.

## Introduce Birta in the user's terms

Present Birta as a place to work together on what people create with agents.
Name the result the user wants: a website, presentation, report, document,
proposal, portfolio, event page, guide, lesson, interactive tool, game or quiz.
Use a few relevant examples when their goal is unknown, rather than listing
everything Birta can do.

Explain the useful loop: publish a version, share the project, discuss changes
on the page, and ask the agent to apply the feedback. Teammates can contribute through
their own connected agents. Versions and feedback stay with the project, and
published updates keep the same address.

Use plain, friendly language and concrete actions. Say "presentation" or
"report", rather than "artifact". Describe what the user can make and who can
review it; keep HTML, Markdown, static hosting, MCP and build details out of the
introduction and goal question. Explain a technical limit only when it affects
the user's request, in terms of what the result can do. Hosting, domains, forms
and statistics support the work; they do not need to lead the introduction.
Describe revisions as something the user asks the agent to do.

## Check the connection

Call the connected Birta tool `list_projects` to check access and find available
projects. Tool names may include the plugin's namespace.

If the tool is unavailable or reports an authentication problem, ask the user to
connect or reconnect Birta through the client's plugin settings and complete the
sign-in flow. Stop dependent work until access is restored. Do not request tokens
or passwords in chat, claim authentication succeeded without a successful call,
or configure a second MCP server as part of setup.

ChatGPT can receive Birta's events; Codex cannot. In ChatGPT, when the user asks to
receive their Birta mentions, subscribe to the `thread.mention` event of the Birta
app and ask the user to confirm it there. The subscription covers every project
where the user may call you, ChatGPT renews it while the app stays connected, and it
ends when the user disconnects Birta. In Codex, and in ChatGPT until the subscription
is confirmed, pick mentions up with `list_mentions`.

## Choose the next step

If the user only asked to run setup, report whether the connection works and ask
what they want to create, share or review, or which existing project they want
to work on. For example: "What would you like to work on first: a presentation,
a report, a website, or something you already made?" Do not
create an empty demo project just to complete onboarding.

Once the user names a goal or a project, continue with the `birta-publish` skill
instead of restarting setup; for access, people, forms, a domain or visitor
stats, with `birta-manage`.
