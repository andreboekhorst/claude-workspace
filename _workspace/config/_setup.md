---
name: setup
description: Initial setup and configuration of the coworking space
trigger: User says "set up my space", "configure", or opens the project for the first time
requirements:
---

# Workflow: Setup

A short, conversational onboarding. Ask one question at a time — wait for an answer before moving on.

---

# Step 1 — Welcome & Environment Check

Show this:

> ## Meeting Notes Coworking Space
> **Your AI note-taking partner**

**Silently do the following** (don't list each folder — just report the result):

1. Verify and create any missing folders:
   - `/meeting-notes`
   - `/_workspace/sources`
   - `/_workspace/logs`

2. Scan workflow files in `/_workspace/workflows/` for requirements. Check availability (e.g. try `gcal_list_calendars` for Google Calendar MCP).

**Then report a compact summary:**

> ✅ Workspace folders — ready
> ✅/⚠️ [Requirement] — [status]
>
> _(If anything is missing, briefly say what's limited and how to fix it. Don't block setup.)_

Then immediately ask the first question (don't wait for the user to respond to the environment check).

---

# Step 2 — Getting to Know You

Ask these questions **one at a time**. Wait for an answer before asking the next. Keep the tone conversational — no numbering, no quiz feel. The user can say "skip" to move on.

**Questions (in order):**

1. **What's your name and role?**
2. **What kind of meetings do you typically have?** (standups, 1:1s, planning, client calls...)
3. **What matters most to you in meeting notes?** (decisions, action items, discussion, open questions — pick your top 2-3)
4. **What language should notes be in?**

That's it — four questions. Use sensible defaults for everything else.

---

# Step 3 — Save & Launch

1. **Save preferences** to `/_workspace/sources/preferences.md`:

```markdown
# User Preferences

## About
- **Name:** [name]
- **Role:** [role]

## Meetings
- **Typical meetings:** [list]
- **Recurring meetings:** [list, or "none specified"]
- **Frequent collaborators:** [names/roles]

## Note-Taking Style
- **Detail level:** [brief / moderate / thorough]
- **Top priorities:** [what matters most in notes]
- **Tone:** [formal / informal / match the meeting]
- **Language:** [language]

## Live Meeting Behaviour
- **Claude's activity level during flow:** [minimal / moderate / active]
- **Auto-flag action items during flow:** [yes / no]

## After the Meeting
- **Auto-suggest open ends:** [yes / no]
- **Auto-add tasks to task list:** [yes / ask first]
```

Use sensible defaults for anything the user skipped. For defaults: moderate detail, action items & decisions as priorities, informal tone, minimal chiming in, auto-flag action items, auto-suggest open ends, ask before adding tasks.

2. **Show the launch screen:**

> ## You're all set!
>
> **Here's what you can do:**
>
> | | Workflow | Trigger |
> |---|---|---|
> | 📝 | **Note-Taking** | _"notes from today's meeting"_ |
> | ✅ | **Tasks** | _"show my action items"_ |
> | 🔮 | **Prepare Meeting** | _"prep me for tomorrow's sync"_ |
> | 📎 | **Add Context** | _"add this document to sources"_ |
>
> **Just tell me about a meeting and we'll go!** ✨

3. Log this setup session to `/_workspace/logs/`.

4. **Comment out the ACTIVATE line at the bottom of `CLAUDE.md`** — wrap it in `<!-- ... -->` so setup does not trigger again. The line should become: `<!-- **ACTIVATE: Setup workflow — read '_workspace/config/_setup.md' and execute.** -->`
