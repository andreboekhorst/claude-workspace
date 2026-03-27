---
name: data-analysis
description: Collect data, find patterns, and present insights that drive decisions.
parameters:
  - data_domain: What domain — sales, operations, user behavior?
  - key_question: What's the main question you're trying to answer?
---

# Data Analysis

**Follow-up:** What data are you working with, and what are you trying to find out?

## Skills

### Research
Gather domain context and background for the analysis.
1. Define the question and scope
2. Collect information from sources
3. Organize findings into themes
4. Deliver summary with gaps flagged

In: topic, constraints | Out: domain context summary → `files/analysis/`

### Synthesize
Combine data from multiple sources into coherent patterns.
1. Identify all inputs (files, references, prior work)
2. Extract key data points from each source
3. Cluster into themes and cross-reference
4. Write thematic summary with attribution

In: multiple sources (CSVs, spreadsheets, images of charts, PDFs) | Out: pattern analysis → `files/analysis/`

### Summarize
Produce executive-level takeaways from detailed analysis.
1. Read the full analysis
2. Extract core findings and decisions
3. Structure into a scannable format
4. Calibrate to target length

In: analysis output | Out: executive summary → `files/reports/`

### Explain
Translate technical findings for a non-technical audience.
1. Clarify topic and audience
2. Identify core concepts and misconceptions
3. Choose analogies that bridge understanding
4. Build explanation layer by layer

In: findings, audience | Out: accessible breakdown → `files/reports/`

### Draft
Write a polished report with narrative and recommendations.
1. Clarify purpose, audience, and format
2. Outline sections and key points
3. Draft full report
4. Review for coherence and completeness

In: analysis, audience | Out: final report → `files/reports/`

## Tools
- **Bash** — run data processing scripts and calculations

## Folders
- `files/data/` — raw datasets, CSVs, spreadsheets, screenshot exports
- `files/analysis/` — scripts, notebooks, intermediate calculations
- `files/reports/` — final reports, chart exports, slide decks
