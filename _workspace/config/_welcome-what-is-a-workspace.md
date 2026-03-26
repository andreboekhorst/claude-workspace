---
name: welcome-what-is-a-workspace
description: Explains what a workspace is — shown from the welcome gate before setup begins
trigger: Internal only — called from _setup.md welcome step
requirements: AskUserQuestion
---

# What Is a Workspace?

Show the following text to the user:

---

A workspace is a folder on your computer that gives Claude everything it needs to help you with a specific job.

Think of it like a desk set up for one type of work. Instead of a blank desk every time, you sit down and everything's already there — your notes, your tools, your process.

A workspace contains:

**Actions** — step-by-step recipes Claude follows on your behalf. "Prep my meeting", "Draft a post", "Review my OKRs" — each one is a small instruction file that tells Claude exactly what to do and how.

**References** — background knowledge that makes actions smarter. Your writing style, company context, a list of clients, a URL you check often. Claude reads these when it needs them.

**Files** — anything you upload or Claude creates. Notes, drafts, exports — all organised in folders that make sense for your work.

It all lives in plain text files you can read and edit. Nothing is locked away.

---

Then use `AskUserQuestion` with the question "Want to explore more or jump in?" and these options:
- How does it work?
- What can I do with it?
- Let's get started!
