---
name: index-files
description: Scan the files/ folder and maintain a quick-reference index in CLAUDE.md so Claude knows when to use which file
trigger: Automatically after files are added/removed, or when user says "index files", "update file index", "refresh files"
requirements: none
---

# Action: Index Files

---

# Role

You are a file indexer. Your job is to scan the `files/` folder, build a concise index of what's there, and write it into CLAUDE.md so that Claude always knows which files are available and when to reference them.

---

# Phase 1 — Scan

Recursively list everything in `files/`. For each file, note:
- **Path** — relative from workspace root
- **What it is** — infer from filename, extension, and a quick read of the first ~20 lines (or file metadata for binaries/images)

Skip `.gitkeep` files and empty directories.

If `files/` is empty or doesn't exist, go straight to Phase 3 (write an empty index).

---

# Phase 2 — Describe

For each file, write a one-line description following this format:

```
- `files/example.pdf` — Project charter; reference when discussing scope or deliverables
```

The description has two parts separated by a semicolon:
1. **What it is** — short factual label
2. **When to use it** — when Claude should pull this file into context

Group files by subfolder if subfolders exist. Keep descriptions tight — one line each, no paragraphs.

---

# Phase 3 — Update CLAUDE.md

Find the `## File Index` section in `CLAUDE.md`. If it doesn't exist, create it right after the `## Folder Structure` section.

Replace the entire contents of `## File Index` with the new index. The section format:

```markdown
## File Index
<!-- Auto-maintained by the index-files action. Do not edit manually. -->

- `files/example.pdf` — Project charter; reference when discussing scope or deliverables
- `files/data/report.csv` — Monthly metrics export; reference for data questions

_Last indexed: YYYY-MM-DD_
```

If no files exist:

```markdown
## File Index
<!-- Auto-maintained by the index-files action. Do not edit manually. -->

(no files yet — upload files to the `files/` folder)

_Last indexed: YYYY-MM-DD_
```

---

# Phase 4 — Confirm

> **File index updated** — [N] file(s) indexed in CLAUDE.md.

List any files that were added or removed since the last index (if you can tell from the previous index). Keep it brief.

---

# Quality Rules

- **Never invent descriptions.** Base them on actual file content/metadata.
- **Keep it scannable.** One line per file, no exceptions.
- **Idempotent.** Running this twice in a row produces the same result.
- **Don't move or modify files.** This action only reads and indexes.
