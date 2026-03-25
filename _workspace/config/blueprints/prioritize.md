---
name: prioritize
type: workflow-blueprint
description: Rank a list of items by defined criteria to determine what to focus on first.
when: User has too many things and needs to focus.
tools: none
---

# Prioritize

A structured ranking workflow that turns a messy backlog into an ordered list. Makes trade-offs visible so the user can commit to a sequence with confidence.

## Typical flow

1. **List** items — collect all items to be prioritized. Clarify scope: is this everything, or a subset?
2. **Define** criteria — agree on 2-4 scoring dimensions. Common defaults: impact (how much does it matter?), effort (how hard is it?), urgency (how time-sensitive is it?).
3. **Score** each item against each criterion. Use a simple scale (1-3 or 1-5). Keep it fast — gut-level scoring is fine for a first pass.
4. **Rank** — calculate a composite score or use a visual matrix (e.g., impact vs. effort). Sort items from highest to lowest priority.
5. **Present** — deliver the ranked list with a brief rationale for the top items and any notable trade-offs.

## Inputs

- A list of items to prioritize (tasks, features, ideas, projects).
- Optional: criteria the user cares about most.
- Optional: constraints (budget, time, capacity) that affect feasibility.

## Outputs

- Prioritized list with scores and rationale.
- Optional: a "not now" list of items explicitly deprioritized, with reasoning.

## Quality signals

- Criteria reflect what the user actually values, not generic defaults.
- Scoring is consistent — similar items score similarly.
- The top 3 items feel right to the user; if not, a criterion is missing.
- Low-priority items have a clear reason for being low, not just low scores.
- The user leaves with a clear "do first" action.

## Common variations

- **Quick stack rank**: skip scoring, just force-rank by gut feel and validate.
- **Impact/effort matrix**: plot items on a 2x2 grid for a visual overview.
- **MoSCoW**: categorize into Must, Should, Could, Won't instead of numeric scoring.
- **Weighted scoring**: assign different weights to criteria when some matter significantly more.
- **Timeboxed prioritization**: prioritize only what fits in a specific time window.
