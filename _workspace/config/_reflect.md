---
name: reflect
description: Review the session and propose workspace improvements — triggered automatically after logging
trigger: Automatically invoked after logging completes — not user-triggered

requirements: none
---

# Skill: Reflect & Improve

This skill runs after every log entry. It briefly reviews what just happened and considers whether the workspace could work better. Most of the time it stays silent — it only speaks up when there's a concrete, actionable improvement to suggest.

---

# What to review

Look at:

1. **The session that just completed** — what skill was used, what went well, what felt clunky or missing.
2. **The log history** — read the current day's log file to spot patterns (e.g. repeated friction, skills always followed by the same manual step, missing skills).
3. **The current skill set** — scan `/_workspace/skills/` and the `### User Skills` section in CLAUDE.md. Are there gaps? Are skills being used as intended?

---

# Types of improvements to look for

- **Missing skill** — the user keeps doing something manually that could be a skill.
- **Skill refinement** — an existing skill is too broad, too narrow, or missing a useful phase.
- **Workflow connection** — two skills that should hand off to each other but don't.
- **Missing reference** — the user keeps providing the same context that could be stored as a reference.
- **Folder structure** — files are ending up in the wrong place or a new subfolder would help.

---

# Rules

- **Skip during initial setup.** If the session that just completed was the Setup skill (`_setup.md`), stay silent and end immediately. Setup is a special case — the workspace is still being configured, so improvement suggestions are premature.
- **Stay silent if there's nothing to improve.** Do not force suggestions. No improvement is the most common outcome — that's fine.
- **Maximum one suggestion per session.** If you spot multiple things, pick the highest-impact one.
- **Be concrete.** "You could add a skill for X" is good. "Maybe consider improving your workflow" is not.
- **Be brief.** One short paragraph maximum. Frame it as a suggestion, not a directive.
- **Never make changes without asking.** Always propose, never act.
- **Don't repeat suggestions.** Check the log for previous reflect entries — if you already suggested something and it wasn't acted on, don't suggest it again.

---

# Output format

If you have a suggestion, present it like this:

```
💡 **Workspace improvement idea:** [one-sentence suggestion]
[1-2 sentences explaining why and what it would look like]
Want me to set this up?
```

If there's nothing to suggest, output nothing. Do not say "no improvements needed" or similar — just stay silent and end the skill.
