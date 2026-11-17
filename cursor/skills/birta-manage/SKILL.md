---
name: birta-manage
description: "Manage a Birta project's settings: who can open it, the people invited and their roles, lead forms and the submissions they collect, a custom domain, visitor stats and the \"made with Birta\" mark. Use when the user asks to open or restrict access to a Birta project, share it with someone by email, add or change a form on the site, read leads, connect their own domain, check visitors, or hide the Birta mark. Publishing and feedback are birta-publish."
---

# Manage a Birta project

Use these tools when the user's request calls for them, not to show them off.
Respond in the user's language. Settings that change who sees the project or what
it costs belong to the project's owner: act only on what the owner asked for, and
report a refusal in plain words. Check the current state with `project_settings`
before changing it. Tool names may include the plugin's namespace. If the Birta
tools are missing or answer with an authentication error, follow the
`birta-setup` skill first.

- **Lead forms.** A form on the site that sends real submissions to the owner:
  declare it first with `create_form` (the form key, field keys, types and choice
  values), then write the markup exactly from the intake contract it returns.
  Change a form with `update_form`; see one with `get_form` or `list_forms`.
  Read submissions with `list_leads` and `get_lead`; they are private data, so
  summarize them only for the person you work for and never put them on the site
  or in a thread.
- **Access and people.** `set_project_access` decides who opens the address:
  invited people only, or anyone with the link, who may view or also comment, and
  whether search engines index it. `share_project` invites people by email as
  editors, commenters or viewers; `change_role` and `revoke_access` adjust that.
  A password on the link is set only by the owner in Birta, never through the agent.
- **Own domain.** `connect_domain` returns the DNS records to set at the
  registrar; pass them on exactly, then call `verify_domain`. One domain per project.
- **Visitors.** `stats` reports visitor totals for a week, month or quarter.
- **Birta mark.** `set_site_mark` shows or hides the small "made with Birta" mark;
  hiding it requires a paid plan, and the answer names the plan when it is not
  allowed.

Publishing a form or any other change to the site goes through the
`birta-publish` skill: edit the draft, then `publish_version`.
