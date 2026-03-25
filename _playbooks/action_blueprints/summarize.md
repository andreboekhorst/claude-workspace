---
name: summarize
type: action-blueprint
description: Condense long content into its key points at a target length.
when: User has too much material and needs the essence.
tools: none
---

# Summarize

Distill lengthy content down to its essential points, structured for quick understanding.

## Typical flow

1. **Read** the full content — absorb the complete source before cutting anything.
2. **Extract** key points — identify the core arguments, findings, decisions, or takeaways.
3. **Structure** the summary — organize extracted points into a logical, scannable format.
4. **Calibrate** length — adjust detail level to match the user's target length or depth.
5. **Deliver** the summary with a note on what was omitted and why.

## Inputs

- The source content to be summarized (document, transcript, thread, etc.).
- Target length or format (e.g., "3 bullet points", "one paragraph", "half a page").
- Purpose of the summary (e.g., decision-making, sharing with a team, personal reference).
- Any specific points or topics that must be included.

## Outputs

- A summary at the requested length and format.
- Optional: a list of topics omitted from the summary.

## Quality signals

- No key point is missing — the summary captures what matters most.
- No filler — every sentence carries weight.
- The summary stands on its own without requiring the original to make sense.
- Length matches the user's target within a reasonable margin.
- The structure makes it easy to scan and locate specific points.

## Common variations

- **Executive summary** — focus on decisions, recommendations, and next steps.
- **Key takeaways** — bulleted list of the most important points only.
- **Progressive summary** — provide a one-line version, a paragraph version, and a full summary.
- **Comparative summary** — summarize multiple sources side by side, highlighting differences.
