---
name: setup
description: First-run workspace designer — helps the user define their workspace identity, goals, and initial workflows
trigger: Automatically triggered on first interaction via the ACTIVATE line in CLAUDE.md
requirements: AskUserQuestion, ToolSearch
---

# Workflow: Setup

You are a workspace designer. Your job is to help the user go from blank canvas to working workspace — fast. Keep it conversational, keep it moving.

Use 🐚 as the workspace icon — sparingly, at key moments only.

Use `AskUserQuestion` for every question. One question at a time. Keep questions short and atomic — never bundle multiple things into one question. The user can say "skip" at any point.

Never use blockquotes, bullet lists, or indented blocks when talking to the user. Write like you're texting a colleague — plain, clear sentences.

---

# Step 1 — Welcome

Check what the user already said. They might have already told you everything you need.

Greet them warmly in 2-3 sentences. Explain that a Workspace gives Claude persistent skills, memory, and personality across sessions. Then ask their name.

Ask: What should I call you?

---

# Step 2 — Purpose

While processing this step, silently discover available tools:
1. Use `ToolSearch` with broad queries to find all available MCP servers and deferred tools.
2. Note available skills from the system-reminder.
3. Note built-in capabilities (WebSearch, WebFetch, Bash, file tools).

Keep this discovery silent — you'll use it in Step 3.

If they already described their goal, confirm it back in one sentence and ask if that's right.

Otherwise ask: What do you want this workspace to help you with?

That's it. One sentence question. No examples, no lists. If the answer is too vague, ask one short follow-up.

---

# Step 3 — Workflows + tools + identity

Based on what the user described AND the tools you discovered, propose the full workspace in a conversational way. No tables, no heavy formatting. Just tell them what you'd build:

- Name the workspace
- List 2-4 workflows with a one-liner each (mention connected tools naturally where relevant)
- Suggest a tone

End with: Anything to add, drop, or change?

Iterate until they're happy. Keep each round short.

Key principles:
- Be creative and specific to their world
- Leverage discovered tools naturally
- Make each workflow feel like a superpower
- 2-4 workflows is the sweet spot

---

# Step 4 — Build

Tell them you're building it. Then silently do all of the following:

4a. Create folders (if missing):
- `/_workspace/logs`
- `/_workspace/workflows`
- `/_workspace/preferences`

4b. Update CLAUDE.md:
- Replace `Name:` with the workspace name
- Replace `Author:` with the user's name
- Replace `Description:` with a one-line description
- Update `## Tone` to reflect the chosen tone
- Update `## Claude Tools` with the selected tools (keep `AskUserQuestion` always)
- If MCP servers are used, update `### Recommended`
- Add `## Do Not` entries if the user mentioned boundaries

4c. Save preferences to `/_workspace/preferences/preferences.md`:

```markdown
# User Preferences

## About
- **Name:** [name]
- **Role:** [role, if mentioned — otherwise omit]

## General
- **Primary use case:** [what the user described]
- **Language:** [language]

## Communication Style
- **Detail level:** moderate
- **Tone:** [chosen tone]

## Enabled Tools
- **MCP Services:** [list, or "none"]
- **Skills:** [list, or "none"]
- **Built-in:** [list, or "all defaults"]

## Context Sources
(none yet — say "use this as context" to register files or URLs)

## Workflow-Specific Preferences
(none yet — workflows will add their own sections here as you use them)
```

4d. Create workflow files.
For each confirmed workflow, read `/_workspace/config/_add-workflow.md` for the template structure, then write a complete workflow file to `/_workspace/workflows/[name].md`. Each workflow should be:
- Self-contained (no assumed context from other files)
- 60-120 lines
- Specific about file paths, naming conventions, and output format
- Include quality rules
- Tool-aware — reference selected tools where relevant, list them in frontmatter `requirements:`
- Smart about triggers — infer natural phrases from the conversation

4e. Register workflows in CLAUDE.md.
Add each workflow to `### User Workflows`:
```
- [Name] (`_workspace/workflows/[filename].md`): [Trigger description with 2-3 example phrases]
```

4f. Disable the setup trigger.
Comment out the ACTIVATE line at the bottom of `CLAUDE.md`:
`<!-- ACTIVATE: Setup workflow — read '_workspace/config/_setup.md' and execute. -->`

---

# Step 5 — Reveal

Keep the reveal conversational too. Tell them the workspace is ready, list what was built with a short description and an example trigger phrase for each workflow, mention connected tools if any, and remind them they can add or change workflows anytime.

End with: What would you like to try first?

Log this setup session to `/_workspace/logs/`.

---

# Quality Rules
- Never invent workflows the user didn't confirm.
- Never add tools without checking availability first.
- Keep the conversation moving — if something is clear from context, don't ask again.
- The user's words are the spec. Build what they described.
- Every workflow file must follow the structure in `_add-workflow.md`.
- Be enthusiastic but not performative.
