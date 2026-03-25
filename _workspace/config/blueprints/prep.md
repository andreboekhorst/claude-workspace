---
name: prep
type: workflow-blueprint
description: Prepare an agenda, talking points, and background material for a meeting.
when: User has an upcoming meeting and wants to be well-prepared.
tools: [Google Calendar]
---

# Prep

Help the user walk into a meeting fully prepared. Produce an agenda, talking points, and any background context they need.

## Typical flow

1. **Understand** the meeting purpose — what kind of meeting is it, who is attending, and what outcome does the user want.
2. **Check** the calendar for meeting details (time, attendees, any existing agenda or description).
3. **Draft** an agenda with time-boxed items, ordered by priority.
4. **Prepare** talking points for each agenda item — key messages the user wants to convey.
5. **Gather** background material: relevant context, open questions from previous meetings, or reference documents.
6. **Compile** everything into a single prep document the user can review before the meeting.
7. **Confirm** with the user — adjust priorities, add missing topics, or remove items.

## Inputs

- Meeting name, date, and attendees (or a calendar event reference)
- The user's goal for the meeting — what does success look like
- Any topics the user already knows they want to cover
- Previous meeting notes or open items, if available

## Outputs

- A meeting prep document containing: agenda, talking points per item, background notes, and open questions
- Saved to `files/` or a location the user specifies

## Quality signals

- The agenda has a clear desired outcome stated at the top
- Each agenda item has a time estimate and an owner or lead
- Talking points are concise — bullet points, not paragraphs
- Background material is summarized, not dumped raw
- Open questions from past meetings are surfaced so nothing falls through the cracks

## Common variations

- **1-on-1 prep**: Focus on relationship and feedback — include check-in questions and career topics
- **Decision meeting**: Structure around the decision to be made — options, criteria, recommendation
- **Status update**: Organize by project or workstream with progress, blockers, and next steps
- **External meeting**: Add context on the other party — who they are, what they care about, history
