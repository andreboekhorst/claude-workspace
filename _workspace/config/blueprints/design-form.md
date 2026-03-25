---
name: design-form
type: workflow-blueprint
description: Create a structured questionnaire or intake form for collecting consistent information.
when: User needs to collect consistent information from people in a repeatable way.
tools: none
---

# Design Form

Build a questionnaire or intake form that collects the right information, in the right order, with minimal friction for the respondent.

## Typical flow

1. **Define** what information needs to be collected and why — what decisions will the answers inform.
2. **Identify** the respondent: who fills this out, what do they know, and how much time will they give it.
3. **Group** questions into logical sections — start easy, build to harder or more sensitive items.
4. **Write** each question clearly: one thing per question, no jargon, no leading language.
5. **Add** logic and branching where needed — skip sections that don't apply, show follow-ups conditionally.
6. **Specify** answer formats: free text, single select, multi-select, scale, date, file upload.
7. **Review** for clarity — read every question as if you know nothing about the topic, then simplify.

## Inputs

- The purpose of the form — what problem it solves or what decision it supports
- Who will fill it out and in what context (internal team, external applicants, customers)
- Any existing forms, templates, or field lists to build from
- Required vs. optional information

## Outputs

- A structured form template in markdown with sections, questions, answer types, and branching logic
- Ready to transfer into a form tool or use as-is for manual collection
- Saved to `files/` or a location the user specifies

## Quality signals

- Every question earns its place — no "nice to have" fields that won't actually be used
- Questions are unambiguous: two people would interpret each question the same way
- The form respects the respondent's time — it can be completed in the estimated duration
- Sensitive questions come after rapport-building ones, not at the start
- Branching logic is documented so the form can be built in any tool

## Common variations

- **Intake form**: Collects initial information to start a process (new client, new project, support request)
- **Survey**: Focuses on opinions and ratings — uses scales and open-ended reflection questions
- **Application form**: Evaluative — structured for scoring and comparison across respondents
- **Feedback form**: Short, focused on a specific experience — keep it under 5 minutes
