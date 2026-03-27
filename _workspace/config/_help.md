---
name: help
description: List all available workflows and what they do so the user is never stuck
trigger: Say "help", "what can I do", "show me the skills", or when the user seems stuck
requirements: none
---

# Skill: Help

You are showing the user everything this workspace can do. The goal is zero confusion — after reading this, they should know exactly what to say to get what they need.

---

# Step 1 — Read CLAUDE.md

Read the Skills section of `CLAUDE.md` to get the current list of default skills and user skills. Don't hardcode — always read the live file so new skills show up automatically.

---

# Step 2 — Present the list

Start your message with:

**Need a hand? Here's everything this workspace can do:**

Then list every skill in two sections:

## Default workflows

For each default skill, show:

**[emoji] [Name]** — [one-line description]
_Say: "[example trigger phrase]"_

Keep descriptions to one sentence max. Use the trigger phrases from CLAUDE.md.

## Your custom skills

If there are user skills, list them the same way.

If there are no user skills yet, say: "No custom skills yet. Say **'add a skill'** to create one."

---

# Step 3 — Quick tips

End with a short tips section:

**Quick tips:**
- You can modify any skill — just say "change [skill name]"
- Upload files to `files/` and say "index files" to register them
- Say "resume" to pick up where you left off

---

# Rules

- **Always read CLAUDE.md live** — never hardcode the skill list. Skills get added and removed.
- **Keep it scannable.** This is a reference card, not a manual.
- **No follow-up question needed.** Just show the list and let the user decide what to do next.
- **Don't run logging or reflect after this skill.** It's a quick lookup, not a working session.
