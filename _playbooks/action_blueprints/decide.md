---
name: decide
type: action-blueprint
description: Frame a choice, weigh trade-offs, and document the decision with rationale.
when: User faces a decision and needs structured thinking.
tools: none
---

# Decide

A structured decision-making action that separates framing from evaluation. Ensures decisions are explicit, comparable, and documented.

## Typical flow

1. **Frame** the question — restate the decision as a single, clear question. Identify who is affected and what success looks like.
2. **Identify** options — list all viable options, including "do nothing." Briefly describe each.
3. **Define** criteria — agree on 3-5 criteria that matter most (e.g., cost, speed, risk, alignment). Assign relative weights if helpful.
4. **Score** each option against the criteria. Use a simple scale (high / medium / low) or numeric rating.
5. **Recommend** — highlight the top option with a summary of why it wins. Note key trade-offs and any reversibility considerations.
6. **Document** — produce a decision record the user can reference later.

## Inputs

- The decision to be made, or enough context to frame it.
- Optional: criteria or constraints the user already has in mind.
- Optional: options the user is already considering.

## Outputs

- Decision record containing: question, options considered, criteria, scoring, recommendation, and trade-offs.

## Quality signals

- The question is framed precisely enough that someone else could evaluate the same options.
- Options include at least one the user had not considered.
- Criteria reflect what actually matters, not just what is easy to measure.
- The recommendation is clear but acknowledges uncertainty honestly.
- The record is useful if revisited weeks later.

## Common variations

- **Quick decision**: skip scoring, just list pros/cons for two options and recommend.
- **Group decision**: include a stakeholder-mapping step before defining criteria.
- **Reversible vs. irreversible**: flag whether the decision is one-way or two-way; adjust rigor accordingly.
- **Decision journal**: append the record to a running log for future review.
