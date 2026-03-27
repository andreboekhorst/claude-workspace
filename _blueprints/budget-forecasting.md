---
name: budget-forecasting
description: Track spending, model scenarios, and produce financial reports.
parameters:
  - scope: What are you budgeting for — department, project, or org?
  - reporting_cycle: How often do you review — weekly, monthly, quarterly?
---

# Budget Forecasting

**Follow-up:** What are you budgeting for?

## Skills

### Research
Gather historical spending data and establish baselines.
1. Define the budget question and scope
2. Collect data from available sources
3. Organize findings by category or time period
4. Summarize with gaps flagged

In: budget question, constraints (spreadsheets, CSVs, PDF reports) | Out: spending baseline → `files/budgets/`

### Compare
Build side-by-side scenario models (best/expected/worst).
1. List the scenarios to compare
2. Set evaluation criteria (cost, risk, feasibility)
3. Score each scenario against criteria
4. Present trade-offs and recommendation

In: budget assumptions, variables | Out: scenario models → `files/forecasts/`

### Summarize
Produce executive budget summaries for stakeholders.
1. Read the full source material
2. Extract key financial takeaways
3. Structure into a scannable format
4. Calibrate length to audience

In: budget data, reports | Out: executive summary → `files/reports/`

### Review
Compare forecast vs. actuals and set next-period priorities.
1. List what was spent vs. planned
2. Check against budget targets
3. Surface variances and blockers
4. Set priorities for next cycle

In: actuals, forecast (spreadsheets, screenshots of dashboards) | Out: variance report → `files/reports/`

### Document
Capture budget assumptions, methodology, and decisions as an SOP.
1. Identify the process to document
2. Gather each step including tacit knowledge
3. Write in clear sequential prose
4. Add edge cases and prerequisites

In: process description, decisions | Out: budget methodology doc → `files/budgets/`

## Tools
- **Spreadsheet tools** (optional) — quantitative modeling and data manipulation

## Folders
- `files/budgets/` — current and historical budgets, allocations, actuals
- `files/forecasts/` — scenario models, projections, variance analyses
- `files/reports/` — formatted reports and presentation-ready materials
