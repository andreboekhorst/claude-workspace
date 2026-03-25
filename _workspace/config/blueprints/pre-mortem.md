---
name: pre-mortem
type: workflow-blueprint
description: Imagine a plan has failed and work backwards to surface risks before they happen.
when: User has a plan and wants to stress-test it before committing.
tools: none
---

# Pre-mortem

A risk-identification workflow that uses prospective hindsight. Instead of asking "what could go wrong," assume the plan has already failed and ask "why did it fail?"

## Typical flow

1. **State** the plan — summarize the plan, its goals, timeline, and key assumptions.
2. **Assume** failure — project forward to the moment the plan has completely failed. Set the scene: "It is [date]. The plan did not work."
3. **Brainstorm** causes — generate as many reasons for failure as possible. Think across categories: people, process, technology, external forces, assumptions.
4. **Rank** by likelihood and impact — score each risk on both dimensions. Focus attention on high-likelihood and high-impact items.
5. **Propose** mitigations — for each top risk, define a concrete preventive action or contingency plan.
6. **Deliver** the risk register — present a clean summary the user can act on.

## Inputs

- A plan, project, or initiative to stress-test.
- Optional: known risks the user has already identified.
- Optional: timeline or milestones to anchor the failure scenario.

## Outputs

- Risk register: a list of risks ranked by likelihood and impact, each with a proposed mitigation.
- Optional: updated plan that incorporates the top mitigations.

## Quality signals

- Risks go beyond the obvious and include second-order failures.
- The "assume failure" framing actually shifts thinking — results differ from a standard risk list.
- Mitigations are specific and actionable, not generic ("communicate better").
- The user identifies at least one risk they had not previously considered.
- Likelihood and impact ratings feel honest, not optimistic.

## Common variations

- **Focused pre-mortem**: constrain to a single category (e.g., only people risks, only technical risks).
- **Timeline pre-mortem**: walk through each milestone and ask "what killed us at this stage?"
- **Stakeholder pre-mortem**: run the exercise from different stakeholder perspectives.
- **Pre-mortem + pre-parade**: after identifying risks, also imagine wild success and ask what enabled it.
