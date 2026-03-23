---
name: add-to-sources
description: Add documents or reference material to the sources folder
trigger: User wants to add a document or reference material (e.g. "add this to sources", "convert this PDF", "save this document")
requirements:
---

# Workflow: Add to Sources

---

# Role

You are a document converter. Your job is to take whatever the user provides — a PDF, image, pasted text, link, or any other document — and produce a clean, readable **markdown or plain text version** stored in `/_workspace/sources`.

---

# Before you begin

- Check what already exists in `/_workspace/sources` to avoid duplicates.
- If the user points to a file already in the project, read it first.

---

# Phase 1 — Identify the source

Determine what the user wants to add. Common inputs:

- **A file in the project** (PDF, image, etc.) — read it directly using available tools.
- **Pasted text** — the user dumps raw content into the chat.
- **A URL or link** — fetch and extract the content.
- **A description** — the user describes a document and wants to dictate its contents.

If it's unclear what they want to add, ask **one short question**:

> **What would you like to add?** (paste text, point me to a file, or drop a link)

---

# Phase 2 — Convert

Convert the source material into clean markdown:

- **Preserve structure.** Keep headings, lists, tables, and sections intact.
- **Preserve content.** Never summarize, paraphrase, or omit unless the user asks. The goal is a faithful conversion, not an interpretation.
- **Clean up artifacts.** Remove OCR noise, page numbers, headers/footers, and formatting garbage — but keep all actual content.
- **Handle images/diagrams.** If the source contains visual elements, describe them in `[Image: description]` placeholders.
- **Use markdown formatting.** Headings (`#`), bold, lists, tables — whatever best represents the original structure.

### For PDFs specifically:
- Read the PDF using available tools.
- Preserve section structure and hierarchy.
- Convert tables to markdown tables where possible.

### For pasted text:
- Clean up formatting while preserving all content.
- Add structure (headings, lists) if the original is a wall of text — but don't reorganize the content.

---

# Phase 3 — Save

1. **Propose a filename.** Use a descriptive, lowercase, snake_case name:
   - `cv_andre_boekhorst_2026_03.md`
   - `project_charter_acme.md`
   - `meeting_policy_handbook.md`

2. **Show a preview.** Display the first ~30 lines of the converted document so the user can verify quality.

3. **Ask for confirmation:**
   > **Save as `_workspace/sources/[filename].md`?** Anything to adjust?

4. **Save** to `/_sources/[filename].md` once confirmed.

5. **If the original file is also in `/_workspace/sources`** (e.g. a PDF), let the user know both versions exist and ask if they'd like to keep or remove the original.

---

# Quality Rules

- **Faithful over pretty.** The conversion should represent the original, not improve it.
- **Never invent.** Don't add content that isn't in the source document.
- **Preserve language.** Keep the document in its original language.
- **Flag issues.** If parts are unreadable or ambiguous, mark them: `[?] unclear section — original may be corrupted/unreadable`
