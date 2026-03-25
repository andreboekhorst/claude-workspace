---
name: explain
type: action-blueprint
description: Break down a complex topic for a specific audience.
when: User needs something complicated made understandable for a particular group.
tools: none
---

# Explain

Turn a complex topic into a clear, layered explanation tailored to a specific audience.

## Typical flow

1. **Clarify** the topic and the target audience (who needs to understand this, and why?)
2. **Assess** the audience's existing knowledge level and relevant mental models
3. **Research** the topic deeply — identify the core mechanism, key concepts, and common misconceptions
4. **Choose** analogies, metaphors, and structures that bridge from what the audience knows to what they need to learn
5. **Build** the explanation layer by layer — start with the simplest accurate version, then add nuance
6. **Test** the explanation for clarity — flag jargon, check logical flow, simplify where possible
7. **Refine** based on the audience's likely follow-up questions

## Inputs

- The topic to explain
- The target audience (role, expertise level, context)
- Optional: specific angle, depth, or format preferences
- Optional: known misconceptions to address

## Outputs

- A clear explanation document tailored to the audience level
- Analogies and examples mapped to the audience's existing knowledge
- Optional: glossary of key terms, further reading suggestions

## Quality signals

- A reader from the target audience could summarize the core idea in one sentence after reading
- No unexplained jargon — every technical term is either avoided or defined on first use
- The explanation builds logically — each section depends only on what came before
- Analogies are accurate enough to be useful without being misleading
- The reader knows what was simplified and where to go deeper

## Common variations

- **ELI5**: Extreme simplification for non-technical audiences
- **Peer explanation**: Same-level explanation emphasizing nuance and edge cases
- **Executive summary**: Focus on implications and decisions, not mechanics
- **Visual explanation**: Structure around diagrams, flowcharts, or mental models
- **Comparative**: Explain by contrasting with something the audience already understands
