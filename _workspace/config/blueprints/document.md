---
name: document
type: workflow-blueprint
description: Write a standard operating procedure so others can follow a process reliably.
when: User needs to capture how something is done so others can follow it.
tools: none
---

# Document

Create a standard operating procedure (SOP) from a process the user knows. The result should let someone unfamiliar with the process execute it correctly.

## Typical flow

1. **Identify** the process to document — name it, state its purpose, and clarify the intended audience.
2. **Interview** the user to gather each step, including tacit knowledge they might skip over.
3. **Write** the procedure in clear, sequential prose with enough context that a reader understands why each step matters.
4. **Add** edge cases, common mistakes, and troubleshooting guidance for steps that tend to go wrong.
5. **Include** prerequisites (tools, access, permissions) and any definitions or jargon the reader needs.
6. **Format** with a consistent structure: title, purpose, scope, prerequisites, procedure steps, troubleshooting, and revision history.
7. **Review** the draft with the user — confirm accuracy, fill gaps, and simplify language.

## Inputs

- The process to document (described verbally or from rough notes)
- Who the audience is and what they already know
- Any existing documentation, however incomplete

## Outputs

- A structured SOP document in markdown with all standard sections
- Saved to `files/` or a location the user specifies

## Quality signals

- A newcomer to the team could follow the procedure without asking questions
- Edge cases and failure modes are addressed, not ignored
- Prerequisites are listed up front so the reader can prepare before starting
- Language is direct and free of unnecessary jargon
- The document states when it was last reviewed and by whom

## Common variations

- **Quick-reference guide**: Condensed version — just the steps, no background
- **Runbook**: Operations-focused, includes rollback steps and escalation paths
- **Policy document**: Adds rationale, authority, and compliance references
- **How-to article**: Lighter tone, aimed at self-service readers rather than team members
