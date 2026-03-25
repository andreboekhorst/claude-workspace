---
name: map
type: workflow-blueprint
description: Lay out phases and milestones for an initiative as a structured roadmap.
when: User needs a visual or structured timeline for a multi-phase effort.
tools: none
---

# Map

Help the user create a phased roadmap that shows how an initiative moves from start to finish, with clear milestones and dependencies.

## Typical flow

1. **Define** the end state — describe what completion looks like.
2. **Break** into phases — group work into 2-5 sequential or overlapping phases.
3. **Set** milestones and dependencies — mark key checkpoints and what blocks what.
4. **Estimate** timing — assign rough durations or target dates to each phase.
5. **Visualize** the roadmap — present it as a structured timeline or table.

## Inputs

- The initiative or project to map.
- Known phases, milestones, or deadlines (if any).
- Dependencies: what must happen before what.
- Team capacity or resource constraints.

## Outputs

- A phased roadmap containing:
  - Phase names with descriptions.
  - Milestones marking phase transitions.
  - Dependencies between phases or milestones.
  - Estimated timing (dates or durations).
  - A summary view (table, list, or ASCII timeline).

## Quality signals

- Phases are distinct — each has a clear start and end condition.
- Dependencies are explicit, not assumed.
- Timing is realistic given known constraints.
- The roadmap is easy to scan at a glance.
- Nothing critical is missing between start and end state.

## Common variations

- **Product roadmap**: Phases map to releases or feature sets.
- **Learning roadmap**: Phases map to skills or knowledge areas.
- **Migration roadmap**: Phases map to system transitions with rollback points.
- **Quarterly roadmap**: Fixed time buckets with flexible scope per phase.
