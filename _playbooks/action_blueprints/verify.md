---
name: verify
type: action-blueprint
description: Fact-check claims against sources and flag gaps or errors
when: The user has claims, data, or statements they want validated before acting on them
tools: [WebSearch, WebFetch]
---

# Verify

## Typical flow
1. **List claims** — Extract each distinct claim or data point to check
2. **Find sources** — Search for authoritative sources that confirm or deny each claim
3. **Rate confidence** — Assign a confidence level to each claim based on evidence
4. **Report** — Present findings with clear verdicts and supporting evidence

## Inputs
- One or more claims, statements, or data points to verify
- Context: where the claims came from, why they matter

## Outputs
- Verification report: each claim listed with verdict, confidence level, and sources
- Confidence scale: Confirmed / Likely true / Uncertain / Likely false / Debunked
- Flagged gaps where no reliable source could be found

## Quality signals
- Each claim is checked independently — one bad claim doesn't taint others
- Sources are authoritative and recent (not outdated stats or dead links)
- Confidence levels are honest — "uncertain" is a valid and useful answer
- The report distinguishes between "no evidence found" and "evidence contradicts"

## Common variations
- Quick spot-check (verify 1-3 specific facts)
- Full audit (systematic review of a document's claims)
- Data validation (check numbers, dates, statistics against original sources)
- Source verification (assess the reliability of the sources themselves)
