---
name: knowledge-base
description: Organize, write, and maintain documentation so knowledge is findable and current.
parameters:
  - knowledge_domain: What kind of knowledge — technical docs, policies, processes?
  - audience: Who needs this — engineers, new hires, customers?
---

# Knowledge Base

**Follow-up:** What kind of knowledge are you organizing, and who needs it?

## Skills

### Document
Write a standard operating procedure from scratch or rough notes.
1. Identify the process, purpose, and audience
2. Gather each step including tacit knowledge
3. Write in clear sequential prose
4. Add edge cases, prerequisites, and troubleshooting

In: process description, audience | Out: SOP document → `files/docs/`

### Edit
Improve existing documentation for clarity and accuracy.
1. Read the original in full
2. Diagnose issues with clarity, flow, or structure
3. Revise while preserving intent
4. Present improved version with change summary

In: existing doc, concerns | Out: revised document → `files/docs/`

### Checklist
Build review and maintenance checklists for documentation.
1. Define the review process
2. Break into discrete, actionable steps
3. Add quality checks at critical points
4. Group into logical sections

In: review process, standards | Out: maintenance checklist → `files/templates/`

### Explain
Break down a complex topic for a specific audience.
1. Clarify topic and audience
2. Identify core concepts and misconceptions
3. Choose analogies that bridge understanding
4. Build explanation layer by layer

In: topic, audience level | Out: accessible explanation → `files/docs/`

### Review
Audit documentation quality and coverage periodically.
1. Review what was updated or added
2. Check against coverage goals
3. Surface gaps or stale content
4. Set priorities for next review cycle

In: doc inventory, quality standards | Out: quality report → `files/docs/`

## Tools
- No external tools required

## Folders
- `files/docs/` — active documentation, the current source of truth
- `files/templates/` — reusable document templates and structural patterns
- `files/archive/` — retired or superseded documents kept for reference
