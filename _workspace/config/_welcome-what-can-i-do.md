---
name: welcome-what-can-i-do
description: Shows what you can do with Workspace Builder — shown from the welcome gate before setup begins
trigger: Internal only — called from _setup.md welcome step
requirements: AskUserQuestion
---

# What Can I Do With Workspace Builder?

Show the following text to the user:

---

Workspace Builder helps you create a workspace tailored to any kind of work. Here are some examples people build:

**For work**
- Meeting prep that pulls your calendar, researches attendees, and drafts an agenda
- Weekly reporting that gathers data and writes your status update
- Client onboarding that turns a brief into a project plan

**For yourself**
- Job interview prep that researches the company and helps you practise answers
- Content creation that drafts, edits, and repurposes posts across channels
- Learning workflows that turn articles into flashcards or summaries

**For teams**
- Sprint planning that reviews tickets and suggests priorities
- Design sprints with structured exercises and captured outcomes
- OKR setting that drafts objectives and stress-tests them

You're not limited to these — if you can describe the work, we can build a workspace for it.

---

Then use `AskUserQuestion` with the question "Want to explore more or jump in?" and these options:
- What is a workspace?
- How does it work?
- Let's get started!
