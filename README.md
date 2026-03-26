![Header](_assets/header.jpg)

# 🐚 Workspace Designer 
With workspace designer you have project-bound actions like in Claude Code, without needing to write any code or prompts yourself! 
- 🔄 Self writing skills - Add and improve any of your skills
- 🧙🏽‍♂️ Setup Wizard — An initial workflow will ask for user settings and check dependencies
- 🏗️ Flexible blueprint — You can use this blueprint for any set of tasks
- 📚 References — Background knowledge and context that helps workflows perform better
- 🔄 Reusable workflows — Define once, use across sessions and workspaces
- 🧠 Logging — References and settings persist between sessions
- 📦 Progressive disclosure — Only loads instructions when needed
- ✏️ No code required — Just markdown files and folders



---

<p align="center">
  <big><big><a href="https://github.com/andreboekhorst/claude-workspace/archive/refs/heads/main.zip">🐚 Download claude-workspace.zip</a></big></big>
</p>

---

## 🚀 Getting Started
1. Download [this workspace](https://github.com/andreboekhorst/claude-workspace/archive/refs/heads/main.zip)
2. Unzip the file
3. Open Claude Desktop, go to Claude Cowork
4. Under the "Projects" section, click the + button to create a new Project
5. Select "Use an existing folder", and select the folder you just unzipped
6. Say hi! A setup wizard will walk you through configuration.



## Workspace Agent Wizard
When you open your emtpy project folder, all you need to do is say Hi. Then a setup wizard will guide you through creating a workspace exactly cathered for your needs. After this, you can continuously update your workspace functionalities. 

## Exporting and reusing
When you are happy with your workspace, you can export and re-use your workspace for others to use. Just ask to export the project. It will strip any personal files from the project and create a zip file. 




# How does it work?
Claude Cowork is basically Claude Code under the hood. That means it can write it's own prompts! With this in mind we created a framework for a workspace that contains a defined structure, and a set of configurations, actions, logs and references. When you run an empty project for the first time, it will use these predefined configurations to help you set up a workspace and set up actions. 

### Progressive disclosure
Another technique that the workspace designer implements is progressive disclosure. This means that whenever you add new actions to your workflow, it does not just add it to the prompt. In the main entry file (CLAUDE.md) we list all of the actions that are available with a reference to the full instructions. 

## Working with skills and connectors. 
There are no limits. 

## Next Steps
I believe that using llms as a package will be the future of using claude, and this is a first step to reaching that. But there is still a lot of opportunities. We have now limited ourselves to writing our own prompts, but why not create your own bash files?

## Security
Always be wary about the code (or prompts) that you are using on your computer! you can check this folder as it is all in markdown files in this project.

---
---

# The  Framework
The Workspace Protocol defines how a folder must be structured so Claude can discover actions, load instructions on demand, and operate as a domain-specific assistant. Any workspace — whether built by hand or generated — should follow this spec.


### Core Concepts

- **CLAUDE.md as entry point** — Claude reads this file upfront. It contains just enough to identify user intent and route to the right action file.
- **Progressive disclosure** — Full action instructions live in separate files and are loaded on-demand. This keeps the initial context small and focused.
- **Actions** — Standalone markdown files that tell Claude exactly what to do. Split into system actions (setup, logging, etc.) and user actions (what makes your workspace unique).
- **References** — Background knowledge, user settings, and context that help actions perform better.


### Folder Structure

Every workspace that follows the protocol looks like this:

```
my-workspace/
  CLAUDE.md                            # Entry point. The only file Claude reads upfront.
  _workspace/
    config/                            # System actions (not user-facing).
      _setup.md                        # Onboarding and configuration.
      _log.md                          # Session logging.
      _add-reference.md                # Reference management.
      _add-action.md                   # Action builder.
      _export-workspace.md             # Export and packaging.
    actions/                           # User-facing actions. One file per action.
      [action-name].md
    references/                        # References and user settings (filled during setup).
      user-settings.md
    logs/                              # Session logs. Gitignored.
```

Rules:
- `_workspace/` is reserved: don't use it for user content
- Files prefixed with `_` are system files
- All user data folders must be gitignored


### CLAUDE.md Spec

The entry point. Claude reads this upfront and uses it to route user intent to action files. It must contain these sections, in order:

#### Header

```markdown
# [Workspace Title]
- Name: [short name]
- Description: [what this workspace does]
- Version: [version number]
- Author: [who made it]
```

#### Requirements

What the workspace needs. Two levels:

- Hard: Won't work without these. Setup should block or warn prominently.
- Recommended: Works without these, but some actions will be limited.

If there are no hard requirements, say so explicitly.

```markdown
## Requirements

### Hard
None — this Workspace works out of the box.

### Recommended
- Google Calendar MCP: Enables calendar-based actions. Without it, actions relying on calendar data require manual input.
```

### Folder Structure

Lists all folders, split into system folders (versioned, part of the template) and user data folders (gitignored, created during setup).

```markdown
## Folder Structure

### System folders (versioned, part of the template)
- `_workspace/config/`: Internal system actions
- `_workspace/actions/`: User-facing action instructions

### User data folders (gitignored, personal to each user)
- `_workspace/references/`: Reference material, background knowledge, and user settings
- `_workspace/logs/`: Session logs
```

### Actions

Maps user intent to action files. Every entry needs a name, a file path, and trigger examples. Split into:

- Default Actions: Setup, Logging, Add Context, Add Action, Export. System actions present in every workspace.
- User Actions: What makes this workspace unique.

Must end with: `Before executing any action, you MUST read its instruction file in full.`

```markdown
## Actions
Claude activates the matching action based on user intent. Read the user's intent and activate automatically — do not wait for a command.

### Default Actions
These are default actions that come with any workspace:
- Setup (`_workspace/config/_setup.md`): Says "set up my space", "configure", or opens the project for the first time.
- Logging (`_workspace/config/_log.md`): Session logging, runs after every action.
- Add Reference (`_workspace/config/_add-reference.md`): Wants to add background knowledge or reference material.
- Add Action (`_workspace/config/_add-action.md`): Wants to add a new action or skill.
- Export Workspace (`_workspace/config/_export-workspace.md`): Wants to export, share, or package the workspace.

### User Actions
- [Action Name] (`_workspace/actions/[filename].md`): [Trigger description with 2-3 example phrases]

Before executing any action, you MUST read its instruction file in full. This is progressive disclosure — the detailed instructions are loaded on-demand, not upfront.
```

### Ground Rules

Must include at least these four:
- User data is sacred: never overwrite or delete without permission
- Never invent: only use what the user actually provided
- Always log sessions: run the logging action after every action
- Read files first: never edit a file you haven't read in this session

Authors can add more.

### Tone

How Claude should communicate. Without it, Claude defaults to generic behavior.

### Do Not

Explicit anti-patterns for this workspace.

### Setup Trigger

Last line. Triggers the setup action on first run, then gets commented out:

```markdown
ACTIVATE: Setup action — read `_workspace/config/_setup.md` and execute.
```


## Action Files

Each action is a standalone markdown file. It should contain everything Claude needs — don't assume context from other files.

Guidelines:
- Be specific: tell Claude what to do, what to ask, what to output, where to save
- Include examples: show expected output format, file naming, templates
- State constraints: if the action has rules, state them explicitly


## Default Actions

Every workspace includes these system actions in `_workspace/config/`:

| Action | File | Purpose |
|--------|------|---------|
| Setup | `_setup.md` | First-run onboarding: verify folders, check requirements, personalize settings, show available actions |
| Logging | `_log.md` | Runs after every action: appends to daily log, records what happened and what changed |
| Add Reference | `_add-reference.md` | Register documents, URLs, or background knowledge as reference material |
| Add Action | `_add-action.md` | Interactively create new actions and register them in CLAUDE.md |
| Export | `_export-workspace.md` | Package the workspace for sharing (clean template or full export) |


---


# Part 2: The Workspace Designer

The Workspace Designer is a starter template that implements the Workspace Protocol. It's a ready-to-use workspace with all the default system actions built in.

## What It Does

- **Setup Wizard** — Walks you through first-time configuration, checks dependencies, saves your settings
- **References** — Add background knowledge and context that helps actions perform better
- **Reusable actions** — Define once, use across sessions
- **Logging** — Automatic session logging so context persists between sessions
- **Self-improving** — Because Claude can read and modify its own instructions, you can continuously improve your workspace while using it
- **No code required** — Just markdown files and folders

## Building Your Own

1. Copy this repo or create the structure from scratch
2. Write your CLAUDE.md following the protocol spec above
3. Create your setup action in `_workspace/config/_setup.md`
4. Add action files to `_workspace/actions/`
5. Zip and share


---


## 🔮 What's Next

This is a draft. We're working toward:
- A skill that generates Workspaces from a description
- A library of community Workspaces
- Native Claude Cowork integration


## FAQ

**Why not just use Claude Skills?**
Claude Skills can be used within the Claude app, but they are not bound to a specific project or action. Also, it is a lot easier to configure new actions within your workspace, and because Claude can change its own instructions — you can continuously improve your actions!

**What is progressive disclosure?**
Progressive disclosure means Claude only loads the instructions it needs, when it needs them. The CLAUDE.md file is lean — it contains just enough to identify user intent and route to the right action. The full instructions for each action are read on-demand when activated. This keeps context small and focused.


## ⚠️ Security Notice

Workspaces are essentially prompt files that instruct Claude how to behave. Before using any Workspace you didn't author yourself, **read every markdown file in the project** — especially `CLAUDE.md` and the action files in `_workspace/`. Treat them like code: a malicious or poorly written prompt could instruct Claude to overwrite files, exfiltrate content, or behave in unexpected ways. Only run Workspaces from sources you trust, and review any changes before applying them to your own setup.
