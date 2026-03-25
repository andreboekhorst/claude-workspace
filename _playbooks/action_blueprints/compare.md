---
name: compare
type: action-blueprint
description: Side-by-side analysis of options, tools, or competitors
when: The user needs to evaluate 2+ options against defined or implied criteria
tools: [WebSearch, WebFetch]
---

# Compare

## Typical flow
1. **Define options** — List the things being compared; clarify scope
2. **Set criteria** — Agree on what matters (cost, quality, speed, etc.)
3. **Gather data** — Research each option against every criterion
4. **Score and present** — Build a comparison matrix, highlight trade-offs
5. **Recommend** — State a recommendation with reasoning, or rank options

## Inputs
- Two or more options to evaluate
- Criteria (explicit or inferred from context)
- Weighting preferences if the user has them

## Outputs
- Comparison table or matrix
- Summary of trade-offs per option
- Clear recommendation with reasoning

## Quality signals
- Every option is evaluated on the same criteria — no gaps in the matrix
- Sources are cited for factual claims (pricing, specs, features)
- Trade-offs are stated honestly — no option is perfect
- Recommendation matches the user's stated priorities, not generic "best"

## Common variations
- Feature comparison (tools, products, services)
- Vendor evaluation (pricing, support, reliability)
- Strategy comparison (approaches, frameworks, methods)
- Quick gut-check (2 options, few criteria) vs. full evaluation (many options, weighted scoring)
