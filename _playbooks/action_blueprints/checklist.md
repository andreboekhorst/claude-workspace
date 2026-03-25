---
name: checklist
type: action-blueprint
description: Turn a process into a reusable, standardized checklist.
when: User has a repeatable process that should be standardized into discrete steps.
tools: none
---

# Checklist

Build a reusable checklist from a process the user describes. The goal is a document someone can follow repeatedly without missing steps.

## Typical flow

1. **Ask** the user to describe the process they want to standardize.
2. **Break** the process into discrete, actionable steps — each step should be a single verb-driven action.
3. **Identify** decision points where the path may branch (if/then logic, conditional steps).
4. **Add** quality checks at critical moments — points where a mistake would be costly.
5. **Group** related steps into logical sections with clear headers.
6. **Format** the result as a markdown checklist with `- [ ]` items, section headers, and any conditional notes.
7. **Review** with the user — walk through the checklist and adjust ordering, granularity, or missing steps.

## Inputs

- A description of the process (verbal, notes, or existing documentation)
- Context: who will use this checklist, how often, and in what setting
- Any known failure points or steps that are commonly skipped

## Outputs

- A markdown checklist document with sections, checkbox items, decision points, and quality checks
- Saved to `files/` or a location the user specifies

## Quality signals

- Every step starts with a clear action verb
- No step requires unstated knowledge — a newcomer could follow it
- Decision points are explicit, not buried inside steps
- The checklist has been reviewed against the original process description
- Critical steps include a brief "why" note where the reason isn't obvious

## Common variations

- **Pre-flight checklist**: Short, run-before-you-go format (no sections, just a flat list)
- **Onboarding checklist**: Multi-day structure with ownership and deadlines per item
- **Audit checklist**: Adds a "status" or "evidence" column alongside each item
- **Conditional checklist**: Heavy branching — use indented sub-lists for if/then paths
