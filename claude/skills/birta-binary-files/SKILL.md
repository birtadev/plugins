---
name: birta-binary-files
description: "Put images, fonts and other binary files into a Birta draft, or read them back: send them over HTTP to an upload address when you can make your own requests, or pass them as base64 text through the file tools when you can't. Use whenever a task adds, replaces or reads a picture, a font, an icon, a PDF download or any other non-text file of a Birta project."
---

# Binary files in a Birta draft

Text files (HTML, CSS, JS, Markdown, SVG, JSON) go through `write_file`, `edit_file`
and `replace_lines` as they are. Everything else is binary: images, fonts, audio,
video, archives offered for download. There are two ways to put one into a draft.

## Choose the way

1. **You can make HTTP requests** (a terminal, `curl`, a script with network access):
   ask for an upload address and send the files to it. This is the default — it is
   fast, exact and costs no tokens for the file's bytes.
2. **You can't** (a chat without network, a sandbox with no way out): write the file
   as base64 text with the file tools, whole or in parts. See the last section.

Both ways need a draft: `list_versions` shows it; `create_version` opens one.

Send the user's file as it is; don't resize or recompress it unless they ask.

If neither way works — no network and no way to read the file's bytes, or a file too
large to write out as base64 yourself — don't publish without it and don't put a
placeholder in its place. Tell the person which file didn't go in and why, and offer:

- attach it in the chat of the Birta panel (the paperclip) and ask Birta's agent there
  to put it into the project;
- or a smaller copy of it — made only with their consent.

## Send files to an upload address

Call `get_upload_address` with the project address and the draft's number. The
answer gives the address, the draft number and the moment it stops working. An
address takes **one** send within **15 minutes**; ask for a new one for every send.
The address is for your own request only: never show it to the person or ask them to
open it, and don't print it into files, pages or commits.

Send either the files themselves or one zip archive.

**Files** — one form part per file; the part's file name is the file's path in the
draft. Best for one to a few files:

```bash
curl -sS -X POST "$UPLOAD_URL" \
  -F "file=@./out/logo.png;filename=images/logo.png" \
  -F "file=@./out/hero.webp;filename=images/hero.webp"
```

**A zip** — paths inside the archive are paths in the draft; the archive's root is
the draft's root. Best for many files gathered with one command:

```bash
(cd site && zip -r -X ../upload.zip images fonts)
curl -sS -X POST "$UPLOAD_URL" -H "content-type: application/zip" --data-binary @upload.zip
```

Rules for both:

- Send only the files that change. A send adds and replaces; it never deletes. Files
  of the draft that are not in the send stay as they are.
- Paths are case-sensitive and relative to the draft root: `images/logo.png`, not
  `/images/logo.png` or `./images/logo.png`.
- No two files with the same path in one send — the whole send is refused.
- Leave out build output folders, version-control folders and secrets (`.env`, keys).
  They are dropped anyway and named in one summary line.
- No symbolic links inside the archive: they are refused as unsafe paths.
- Only form parts and zip archives are read; tar, gzip and 7z are not.

## Read the answer

The answer is JSON:

| Field | Meaning |
| --- | --- |
| `refused` | `true` when nothing was written |
| `reason` | Why it was refused, as a code; empty otherwise |
| `version` | The draft's number |
| `written` | `[{path, bytes}]` — files now in the draft |
| `rejected` | `[{path, reason}]` — files not written; the rest of the send was |
| `excluded` | One line naming junk and secrets left out |
| `repeat` | `true` when this is the stored answer of an earlier send |
| `text` | The same in one or two sentences |

A send with at least one written file is a success even if some files were
rejected. Fix the rejected ones (type, path, size) and send them again **to a new
address**. If every file was rejected, the answer is a refusal with reason
`validation_failed` and the draft is unchanged.

Check the result with `list_files`, or open the draft's preview.

## When the address doesn't take the send

| `reason` | What to do |
| --- | --- |
| `repeat: true` in the answer | The address was used already; the answer is that first send's. Nothing new was read. Ask for a new address to send again. |
| `wrong_state` | The address expired, or the draft was published or discarded. Check `list_versions` and ask for a new address for the current draft. |
| `busy` | Another send to this address is still being received. Wait for its answer instead of sending again. |
| `failed` | The send didn't arrive in time, broke off, or storing failed. Nothing was written and the address is still valid: send again to it. |
| `too_many` | More files than one package may hold. Split into several sends, each to a new address. |
| `plan_limit` | Bigger than the space the owner's plan gives one project. Send less at once, or tell the owner what the answer says about plans. |
| `no_such_project`, `role_too_low`, `account_banned`, `project_blocked`, `external_build` | The same refusal a file edit gets. Tell the owner the answer's text. |

An address that was never issued, or a mistyped one, answers 404 with no fields.

## Without network: base64 through the file tools

A binary file is base64 text on `write_file`, `replace_lines` and `read_file`: it is
decoded on write and encoded again on read, wrapped at 1024 characters per line.

- Small file: `write_file` with the whole base64 text as `content`.
- Large file: write the first part with `write_file`, then append each next part with
  `replace_lines` after the last line. Cut parts **only on whole lines** of the
  encoded text (or on a multiple of 4 characters). Encode the file once and cut that
  text; parts encoded separately don't join back into a valid file.
- A large file makes a long call. Whenever you have network, use the upload address
  instead.
- Never edit the encoded text by hand, re-wrap it, or add spaces: one wrong
  character breaks the file. To change a picture, replace the whole file.
- `edit_file` is for text; a fragment of encoded text is rarely unique.
- SVG is text: write it as markup, not base64.
