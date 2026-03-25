---
name: resume
description: Resume a workspace session — review logs, scan files, and propose next steps
trigger: Say "resume", "where was I", "what's next", or start a new session without clear intent
requirements: AskUserQuestion
---

# Action: Resume

You are picking up where the user left off. Your job is to quickly orient yourself and the user, then propose concrete next steps.

---

# Step 1 — Check workspace state

Silently gather context before saying anything:

## Read recent logs

1. List files in `/_workspace/logs/` and read the **most recent 2-3 log files** (by date).
2. Extract: which actions ran, what artifacts were created, and any **open threads**.

## Scan files

1. Check `files/` for any new or recently modified files.
2. Check `/_workspace/references/` for registered references.
3. Check `/_workspace/actions/` for available user actions.

## Check workspace identity

1. Read the top of `CLAUDE.md` — is the workspace configured (name, description, author filled in)?
2. If the ACTIVATE line is still uncommented, the workspace has never been set up.

---

# Step 2 — Present the situation

Start your message with:

**🔄 Picking up where you left off...**

Then present what you found, in this order:

## If the workspace has never been set up

Say something like: "This workspace hasn't been configured yet. Want to run the setup to get started?"

If there are existing user actions or files despite no setup, mention those too — the user may have been working manually.

## If the workspace is set up

### Last session summary
Summarize the most recent log entry in 2-3 sentences. Focus on what was done and what was left open.

### Open threads
If any log entries have open threads, list them as bullets. These are the most actionable items.

### Recent files
If new files appeared since the last log, mention them — the user may have added something between sessions.

---

# Step 3 — Propose next steps

Based on what you found, propose **2-3 concrete next steps**. Use `AskUserQuestion` with these as options (plus an "Other" option).

## Priority order for suggestions

1. **Open threads** from logs — unfinished work comes first
2. **New files** that haven't been processed — the user may have uploaded something to work with
3. **Available actions** — suggest the most relevant ones based on recent activity
4. **General options** — "add a reference", "create a new action", etc.

## If there's nothing to go on

If there are no logs, no files, and no actions (but the workspace is set up), propose:
- Try one of the available actions (list them)
- Add reference material to make actions smarter
- Create a new action

If the workspace isn't set up at all, propose running setup.

---

# Rules

- **Be brief.** This is a quick orientation, not a report. Keep the whole message under 15 lines.
- **Be factual.** Only reference things you actually found in logs and files.
- **Don't recap everything.** Focus on what's actionable — skip completed work unless it provides context for open threads.
- **Respect the user's time.** If there's an obvious next step, lead with it. Don't make them read through options when the answer is clear.
- **Never fabricate log entries or file contents.** If you can't find logs, say so.
