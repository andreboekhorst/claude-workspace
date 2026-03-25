---
name: brainstorm
type: action-blueprint
description: Generate ideas through divergent thinking, then converge on the strongest ones.
when: User needs creative options before committing to a direction.
tools: none
---

# Brainstorm

A structured ideation action that separates idea generation from idea evaluation. First go wide, then go narrow.

## Typical flow

1. **Seed** the topic — clarify the challenge, goal, or question the brainstorm addresses. Restate it as a clear prompt.
2. **Diverge** — generate as many ideas as possible without judgment. Aim for quantity over quality. Use different lenses (analogy, inversion, constraint removal) to push beyond the obvious.
3. **Cluster** — group related ideas into themes. Label each cluster with a short descriptor.
4. **Converge** — evaluate clusters and individual ideas against the user's goals. Select the top 3-5 strongest ideas.
5. **Present** — deliver the shortlist with a one-sentence rationale for each pick.

## Inputs

- A topic, challenge, or question to brainstorm around.
- Optional: constraints, audience, or goals to guide idea generation.
- Optional: number of ideas the user wants in the final shortlist.

## Outputs

- Full list of generated ideas, grouped by theme.
- Shortlist of strongest ideas with rationale for each selection.

## Quality signals

- The diverge phase produced genuinely varied ideas, not just variations on a single theme.
- Clusters feel distinct and meaningful, not forced.
- The final shortlist is defensible — each pick has a clear reason.
- The user feels the process surfaced ideas they would not have reached alone.

## Common variations

- **Time-boxed brainstorm**: limit divergence to a fixed number of ideas (e.g., 20 in 5 minutes).
- **Reverse brainstorm**: generate ideas for how to make the problem worse, then invert them.
- **Constraint brainstorm**: add an artificial constraint (half the budget, half the time) to force creative thinking.
- **Role-based brainstorm**: generate ideas from different personas or stakeholder perspectives.
