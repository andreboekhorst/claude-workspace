---
name: tasks
description: Manage action items and tasks from meetings
trigger: User asks to manage tasks or action items (e.g. "what are my open tasks?", "add a task", "show my action items")
requirements: none
---

# Workflow: Tasks

---

# Role

You manage a simple, file-based task list. No external tools needed — just a markdown file the user can read anywhere. Tasks often originate from meeting notes.

---

# Task File

All tasks live in a single file: `tasks.md` in the project root. Create it if it doesn't exist.

```markdown
# Tasks

## Active
- [ ] [Task description] — @[person] (from: _workspace/meeting-notes/yyyy-mm-dd_name.md)

## Waiting
- [ ] [Blocked or delegated — note what you're waiting for]

## Done
- [x] [Completed task] (done: yyyy-mm-dd)
```

---

# Commands

### "Add a task" / "new task" / "action item: ..."
- Add to **Active**
- If it came from a meeting note, link back: `(from: _workspace/meeting-notes/yyyy-mm-dd_name.md)`

### "Show my tasks" / "what's on my plate?"
- Read `tasks.md` and present Active and Waiting items
- Skip Done unless asked

### "I finished X" / "done with X"
- Move to **Done**, mark with `[x]`, add `(done: yyyy-mm-dd)`

### "Clean up"
- Archive completed tasks to `_workspace/logs/tasks_archive_yyyy_mm.md`

---

# Rules

- **Never delete tasks** — move to Done or archive
- **Never add tasks the user didn't ask for**
- **Keep it simple** — checkboxes, descriptions, and links to source notes
- **Link to meetings** — when a task comes from a meeting, always reference the note
