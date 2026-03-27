---
name: process-improvement
description: Audit a process, identify waste, then redesign and document the improved version.
parameters:
  - process_name: Which process are you improving?
  - current_pain: What's the biggest pain point right now?
---

# Process Improvement

**Follow-up:** Which process are you looking at?

## Skills

### Research
Map the current process end-to-end.
1. Define the process scope and boundaries
2. Gather information from stakeholders and docs
3. Organize into a step-by-step flow
4. Flag gaps and assumptions

In: process name, stakeholder input | Out: current-state process map → `files/audits/`

### Evaluate
Identify bottlenecks, waste, and friction points.
1. Frame the evaluation question neutrally
2. Map arguments for and against each step's value
3. Rate severity and frequency of issues
4. Conclude with prioritized problem list

In: process map, pain points | Out: bottleneck analysis → `files/audits/`

### Decide
Prioritize which improvements to pursue.
1. Frame the decision as a clear question
2. List improvement options including "do nothing"
3. Score against criteria (impact, effort, risk)
4. Recommend with trade-offs noted

In: problem list, constraints | Out: improvement recommendations → `files/proposals/`

### Document
Write the redesigned process as a standard operating procedure.
1. Identify the process and intended audience
2. Gather each step including edge cases
3. Write in clear sequential prose
4. Add prerequisites and troubleshooting

In: redesigned process | Out: new SOP → `files/procedures/`

### Checklist
Create an implementation and adoption checklist.
1. Map the rollout process end-to-end
2. Break into discrete steps with owners
3. Add quality checks at critical points
4. Group into phases (pilot, rollout, review)

In: improvement plan | Out: implementation checklist → `files/proposals/`

## Tools
- No external tools required

## Folders
- `files/audits/` — current-state process maps, gap analyses
- `files/proposals/` — improvement recommendations, implementation plans
- `files/procedures/` — final documented procedures and SOPs
