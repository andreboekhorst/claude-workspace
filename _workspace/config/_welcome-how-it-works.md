---
name: welcome-how-it-works
description: Explains how the workspace builder works — shown from the welcome gate before setup begins
trigger: Internal only — called from _setup.md welcome step
requirements: AskUserQuestion
---

# How It Works

Show the following text to the user:

---

A workspace is a folder that turns Claude into a specialised coworker for one specific job. Instead of starting from scratch every conversation, your workspace remembers what you're working on, how you like to work, and what tools to use.

Here's the basic idea:

1. **You describe your work** — what you're trying to get done, what's annoying, what takes too long
2. **We design actions together** — small, focused recipes that Claude follows on your behalf (like "prep for a meeting" or "draft a LinkedIn post")
3. **You use them** — just say what you need in plain language and the right action kicks in
4. **It gets better over time** — add references, tweak actions, create new ones as your workflow evolves

Everything lives in this folder. Nothing is hidden, nothing is magic — you can read and edit any file.

---

Then use `AskUserQuestion` with the question "Want to explore more or jump in?" and these options:
- What is a workspace?
- What can I do with it?
- Let's get started!
