![Header](_assets/header.jpg)

## STEP 1 -> USe a template or setup your own!! Strong
## I actually think the template should NOT be in config. 
## since its basically not part of the spec. 

# 🐚 Claude Workspace

A **Workspace** is a structured folder that turns Claude into a domain-specific assistant. It works with Claude Cowork — open a folder, and Claude follows the instructions inside.

This repository contains two things:

1. **The Workspace Protocol** — a spec for how any workspace should be structured so Claude can understand and operate it
2. **The Workspace Designer** — a starter template that implements the protocol, with built-in workflows to help you build and customize your own workspace

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


---


# Part 1: The Workspace Protocol

The Workspace Protocol defines how a folder must be structured so Claude can discover workflows, load instructions on demand, and operate as a domain-specific assistant. Any workspace — whether built by hand or generated — should follow this spec.


## Core Concepts

- **CLAUDE.md as entry point** — Claude reads this file upfront. It contains just enough to identify user intent and route to the right workflow file.
- **Progressive disclosure** — Full workflow instructions live in separate files and are loaded on-demand. This keeps the initial context small and focused.
- **Workflows** — Standalone markdown files that tell Claude exactly what to do. Split into system workflows (setup, logging, etc.) and user workflows (what makes your workspace unique).
- **References** — Background knowledge, user settings, and context that help workflows perform better.


## Folder Structure

Every workspace that follows the protocol looks like this:

```
my-workspace/
  CLAUDE.md                            # Entry point. The only file Claude reads upfront.
  _workspace/
    config/                            # System workflows (not user-facing).
      _setup.md                        # Onboarding and configuration.
      _log.md                          # Session logging.
      _add-reference.md                # Reference management.
      _add-workflow.md                 # Workflow builder.
      _export-workspace.md             # Export and packaging.
    workflows/                         # User-facing workflows. One file per workflow.
      [workflow-name].md
    references/                        # References and user settings (filled during setup).
      user-settings.md
    logs/                              # Session logs. Gitignored.
```

Rules:
- `_workspace/` is reserved: don't use it for user content
- Files prefixed with `_` are system files
- All user data folders must be gitignored


## CLAUDE.md Spec

The entry point. Claude reads this upfront and uses it to route user intent to workflow files. It must contain these sections, in order:

### Header

```markdown
# [Workspace Title]
- Name: [short name]
- Description: [what this workspace does]
- Version: [version number]
- Author: [who made it]
```

### Requirements

What the workspace needs. Two levels:

- Hard: Won't work without these. Setup should block or warn prominently.
- Recommended: Works without these, but some workflows will be limited.

If there are no hard requirements, say so explicitly.

```markdown
## Requirements

### Hard
None — this Workspace works out of the box.

### Recommended
- Google Calendar MCP: Enables calendar-based workflows. Without it, workflows relying on calendar data require manual input.
```

### Folder Structure

Lists all folders, split into system folders (versioned, part of the template) and user data folders (gitignored, created during setup).

```markdown
## Folder Structure

### System folders (versioned, part of the template)
- `_workspace/config/`: Internal system workflows
- `_workspace/workflows/`: User-facing workflow instructions

### User data folders (gitignored, personal to each user)
- `_workspace/references/`: Reference material, background knowledge, and user settings
- `_workspace/logs/`: Session logs
```

### Workflows

Maps user intent to workflow files. Every entry needs a name, a file path, and trigger examples. Split into:

- Default Workflows: Setup, Logging, Add Context, Add Workflow, Export. System workflows present in every workspace.
- User Workflows: What makes this workspace unique.

Must end with: `Before executing any workflow, you MUST read its instruction file in full.`

```markdown
## Workflows
Claude activates the matching workflow based on user intent. Read the user's intent and activate automatically — do not wait for a command.

### Default Workflows
These are default workflows that come with any workspace:
- Setup (`_workspace/config/_setup.md`): Says "set up my space", "configure", or opens the project for the first time.
- Logging (`_workspace/config/_log.md`): Session logging, runs after every workflow.
- Add Reference (`_workspace/config/_add-reference.md`): Wants to add background knowledge or reference material.
- Add Workflow (`_workspace/config/_add-workflow.md`): Wants to add a new workflow or skill.
- Export Workspace (`_workspace/config/_export-workspace.md`): Wants to export, share, or package the workspace.

### User Workflows
- [Workflow Name] (`_workspace/workflows/[filename].md`): [Trigger description with 2-3 example phrases]

Before executing any workflow, you MUST read its instruction file in full. This is progressive disclosure — the detailed instructions are loaded on-demand, not upfront.
```

### Ground Rules

Must include at least these four:
- User data is sacred: never overwrite or delete without permission
- Never invent: only use what the user actually provided
- Always log sessions: run the logging workflow after every workflow
- Read files first: never edit a file you haven't read in this session

Authors can add more.

### Tone

How Claude should communicate. Without it, Claude defaults to generic behavior.

### Do Not

Explicit anti-patterns for this workspace.

### Setup Trigger

Last line. Triggers the setup workflow on first run, then gets commented out:

```markdown
ACTIVATE: Setup workflow — read `_workspace/config/_setup.md` and execute.
```


## Workflow Files

Each workflow is a standalone markdown file. It should contain everything Claude needs — don't assume context from other files.

Guidelines:
- Be specific: tell Claude what to do, what to ask, what to output, where to save
- Include examples: show expected output format, file naming, templates
- State constraints: if the workflow has rules, state them explicitly


## Default Workflows

Every workspace includes these system workflows in `_workspace/config/`:

| Workflow | File | Purpose |
|----------|------|---------|
| Setup | `_setup.md` | First-run onboarding: verify folders, check requirements, personalize settings, show available workflows |
| Logging | `_log.md` | Runs after every workflow: appends to daily log, records what happened and what changed |
| Add Reference | `_add-reference.md` | Register documents, URLs, or background knowledge as reference material |
| Add Workflow | `_add-workflow.md` | Interactively create new workflows and register them in CLAUDE.md |
| Export | `_export-workspace.md` | Package the workspace for sharing (clean template or full export) |


---


# Part 2: The Workspace Designer

The Workspace Designer is a starter template that implements the Workspace Protocol. It's a ready-to-use workspace with all the default system workflows built in.

## What It Does

- **Setup Wizard** — Walks you through first-time configuration, checks dependencies, saves your settings
- **References** — Add background knowledge and context that helps workflows perform better
- **Reusable workflows** — Define once, use across sessions
- **Logging** — Automatic session logging so context persists between sessions
- **Self-improving** — Because Claude can read and modify its own instructions, you can continuously improve your workspace while using it
- **No code required** — Just markdown files and folders

## Building Your Own

1. Copy this repo or create the structure from scratch
2. Write your CLAUDE.md following the protocol spec above
3. Create your setup workflow in `_workspace/config/_setup.md`
4. Add workflow files to `_workspace/workflows/`
5. Zip and share


---


## 🔮 What's Next

This is a draft. We're working toward:
- A skill that generates Workspaces from a description
- A library of community Workspaces
- Native Claude Cowork integration


## FAQ

**Why not just use Claude Skills?**
Claude Skills can be used within the Claude app, but they are not bound to a specific project or workflow. Also, it is a lot easier to configure new workflows within your workspace, and because Claude can change its own instructions — you can continuously improve your workflow!

**What is progressive disclosure?**
Progressive disclosure means Claude only loads the instructions it needs, when it needs them. The CLAUDE.md file is lean — it contains just enough to identify user intent and route to the right workflow. The full instructions for each workflow are read on-demand when activated. This keeps context small and focused.


## ⚠️ Security Notice

Workspaces are essentially prompt files that instruct Claude how to behave. Before using any Workspace you didn't author yourself, **read every markdown file in the project** — especially `CLAUDE.md` and the workflow files in `_workspace/`. Treat them like code: a malicious or poorly written prompt could instruct Claude to overwrite files, exfiltrate content, or behave in unexpected ways. Only run Workspaces from sources you trust, and review any changes before applying them to your own setup.
