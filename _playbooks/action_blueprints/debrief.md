---
name: debrief
type: action-blueprint
description: Process raw notes from a meeting or event into structured decisions, actions, and open items.
when: User has unstructured notes from a meeting or event and needs clarity.
tools: none
---

# Debrief

Take messy, unstructured notes and turn them into a clean record of what was decided, what needs to happen next, and what remains unresolved.

## Typical flow

1. **Read** the raw notes in full — do not summarize prematurely.
2. **Extract** decisions: any commitment, agreement, or conclusion that was reached.
3. **Extract** action items: tasks with a clear owner and, where possible, a deadline.
4. **Identify** open questions: topics raised but not resolved, items deferred to later.
5. **Note** key context: important background, quotes, or reasoning that should be preserved.
6. **Format** everything into a structured debrief document with clearly labeled sections.
7. **Review** with the user — confirm the extracted items are accurate and nothing was missed.

## Inputs

- Raw notes (pasted text, uploaded file, or verbal summary)
- Context about the meeting or event (who attended, what the purpose was)
- Any prior action items or decisions that should be checked for follow-up

## Outputs

- A structured debrief document with sections for: summary, decisions, action items, open questions, and key context
- Each action item includes an owner and deadline where known
- Saved to `files/` or a location the user specifies

## Quality signals

- Every decision is stated as a clear, unambiguous commitment
- Action items are specific enough to act on — verb, object, owner, deadline
- Open questions are genuine unknowns, not just vague topics
- Nothing from the raw notes is silently dropped — if something is excluded, it is trivial
- The debrief is short enough to skim in under two minutes

## Common variations

- **Retrospective debrief**: Focus on what went well, what didn't, and what to change
- **Workshop debrief**: Organize by activity or exercise, capture outputs and themes
- **Incident debrief**: Timeline-based, with root cause, impact, and follow-up actions
- **Interview debrief**: Structured around evaluation criteria and hiring recommendation
