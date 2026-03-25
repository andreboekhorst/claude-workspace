---
name: research
type: action-blueprint
description: Deep dive into a topic, produce a structured summary
when: The user needs to investigate a subject, gather information from multiple sources, and deliver organized findings
tools: [WebSearch, WebFetch]
---

# Research

## Typical flow
1. **Scope** — Define the question, constraints, and depth
2. **Gather** — Collect information from sources
3. **Structure** — Organize findings into themes or sections
4. **Deliver** — Write up summary, cite sources, flag gaps

## Inputs
- A topic or question to investigate
- Constraints: depth, angle, audience

## Outputs
- Structured summary document with sources cited

## Quality signals
- Distinguishes facts from interpretation
- Cites where information came from
- Flags gaps or conflicting findings
- Matches requested depth — doesn't over-research simple questions

## Common variations
- Quick scan (shallow pass) vs. deep dive (comprehensive)
- Internal research (within existing files/references) vs. external (web)
- Comparative research (naturally overlaps with Compare blueprint)
