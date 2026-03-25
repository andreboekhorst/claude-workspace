---
name: evaluate
type: workflow-blueprint
description: Structured pros/cons argument mapping for a specific question to reach a balanced conclusion.
when: User needs to think through both sides of an issue.
tools: none
---

# Evaluate

A structured argument-mapping workflow that forces balanced consideration of both sides before reaching a conclusion. Prevents premature commitment to one position.

## Typical flow

1. **State** the question — frame the issue as a clear yes/no or either/or question. Neutral framing matters.
2. **Map** arguments for — list all arguments supporting one side. For each, note the underlying assumption and strength (strong, moderate, weak).
3. **Map** arguments against — list all arguments supporting the other side with the same structure. Push for equal depth on both sides.
4. **Weigh** strength — compare the arguments directly. Identify which hold up under scrutiny and which rely on weak assumptions.
5. **Conclude** — state a position with appropriate confidence. Flag remaining uncertainties and conditions that would change the conclusion.

## Inputs

- A question, proposition, or issue to evaluate.
- Optional: the user's current leaning (helps ensure the opposing side gets proper attention).
- Optional: specific concerns or arguments the user wants examined.

## Outputs

- Argument map: two structured lists (for and against) with strength ratings.
- Weighted conclusion with confidence level and key uncertainties.

## Quality signals

- Both sides are represented with genuine strength — no straw-manning.
- The user's initial leaning was challenged, not just confirmed.
- Argument strengths are based on evidence quality and logical soundness, not just count.
- The conclusion acknowledges what would need to be true for the other side to win.
- Uncertainties are named explicitly, not hidden in vague language.

## Common variations

- **Steel-man evaluation**: start by building the strongest possible case for the side the user disagrees with.
- **Multi-option evaluation**: extend beyond two sides to evaluate three or more positions.
- **Evidence-weighted**: require each argument to cite a specific fact, example, or data point.
- **Stakeholder lens**: evaluate the question from multiple stakeholder perspectives before concluding.
- **Conditional conclusion**: instead of a single answer, map out "if X then yes, if Y then no" scenarios.
