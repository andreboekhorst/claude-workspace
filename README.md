![Header](_assets/header.jpg)

# Claude Workspace - A Proposal

A Workspace is like a container for your Claude Cowork Projects:
- You can configure it for any workflow
- Your workspace is shareable and reusable
- You can continuously improve your workspace while using it!

Claude Cowork leverages the power of Claude Code while working in the Claude App. Unfortunately it is missing some features like project-specific skills, memory, or workflows.

That's why we're proposing a blueprint for a Claude Workspace: a folder that turns Claude into a domain-specific assistant. A project that can just be opened as a folder within Claude. This project can have **multiple workflows** that are available to you.

This repository is both the spec and a starter template. Everything here demonstrates the patterns any Workspace should follow.

<p align="center">
  <big><big><a href="https://github.com/andreboekhorst/claude-workspace/archive/refs/heads/main.zip">🐚 Download claude-workspace.zip</a></big></big>
</p>


## ✨ Key Features

- 🏗️ **Flexible blueprint** — You can use this blueprint for any set of tasks
- 🧙🏽‍♂️ **Setup Wizard** — An initial workflow will ask for user preferences and check dependencies
- 📚 **Context** — A custom context folder for reference material and domain knowledge
- 🔄 **Reusable workflows** — Define once, use across sessions and workspaces
- 🧠 **Logging** — Context and preferences persist between sessions
- 📦 **Progressive disclosure** — Only loads instructions when needed
- ✏️ **No code required** — Just markdown files and folders


## 🚀 Getting Started

1. Download [this workspace](https://github.com/andreboekhorst/claude-workspace/archive/refs/heads/main.zip)
2. Unzip the file
3. Open Claude Desktop, go to Claude Cowork
4. Under the "Projects" section, click the + button to create a new Project
5. Select "Use an existing folder", and select the folder you just unzipped
6. Say hi! A setup wizard will walk you through configuration.

## How does it work?
Workspaces are designed for Claude Cowork, a feature in the Claude Desktop app that lets you open a folder as a project. When Claude Cowork opens a folder, it reads the CLAUDE.md file and follows the instructions inside. When needed it can read project-specific workflows for instructions that you give it, using a method called progressive disclosure.


## 📁 Structure

Every Workspace looks like this:

```
my-workspace/
  CLAUDE.md                            # Entry point. The only file Claude reads upfront.
  _workspace/
    config/                            # System workflows (not user-facing).
      _setup.md                        # Onboarding and configuration.
      _log.md                          # Session logging.
      _add-context.md                  # Document conversion.
      _add-workflow.md                 # Workflow builder.
      _export-workspace.md             # Export and packaging.
    workflows/                         # User-facing workflows. One file per workflow.
      [workflow-name].md
    preferences/                       # User preferences (filled during setup).
      preferences.md
    logs/                              # Session logs. Gitignored.
    context/                           # Reference material and domain knowledge. Gitignored.
```

Rules:
- `_workspace/` is reserved: don't use it for user content
- Files prefixed with `_` are system files
- All user data folders must be gitignored


## 📄 CLAUDE.md

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
- `_workspace/context/`: Reference material, background documents, and domain knowledge
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
- Setup (`_workspace/config/_setup.md`): Says "set up my space", "configure", or opens the project for the first time. System workflow.
- Logging (`_workspace/config/_log.md`): Session logging, runs after every workflow. System workflow.
- Add Context (`_workspace/config/_add-context.md`): Wants to add a document or reference material (e.g. "add this to context", "convert this PDF", "save this document"). System workflow.
- Add Workflow (`_workspace/config/_add-workflow.md`): Wants to add a new workflow or skill (e.g. "add a workflow", "I want a new skill", "create a workflow for X"). System workflow.
- Export Workspace (`_workspace/config/_export-workspace.md`): Wants to export, share, or package the workspace (e.g. "export my workspace", "create a template", "zip this workspace"). System workflow.

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

```markdown
## Ground Rules
- Notes belong to the user: Never overwrite or delete existing notes without explicit permission.
- Never invent: Only capture what the user actually said or provided. Don't add information that wasn't provided.
- Always log sessions: After completing any workflow, read and execute `_workspace/config/_log.md` to append an entry to the daily log. No log = session not finished.
- Read files first: Before modifying any existing file, ALWAYS read it first. Never append to a file you haven't read in this session.
```

### Tone

How Claude should communicate. Without it, Claude defaults to generic behavior.

```markdown
## Tone
- Clear and direct
- Match the user's energy: brief when they're brief, detailed when they want depth
- Keep responses scannable: headers, short paragraphs, whitespace
```

### Do Not

Explicit anti-patterns for this workspace.

```markdown
## Do Not
- Ask for input for the sake of asking a question when the answer is already implied by the user.
- Invent information or add content the user didn't provide.
```

### Setup Trigger

Last line. Triggers the setup workflow on first run, then gets commented out:

```markdown
ACTIVATE: Setup workflow — read `_workspace/config/_setup.md` and execute.
```


## 📝 Workflow Files

Each workflow is a standalone markdown file. It should contain everything Claude needs — don't assume context from other files.

Guidelines:
- Be specific: tell Claude what to do, what to ask, what to output, where to save
- Include examples: show expected output format, file naming, templates
- State constraints: if the workflow has rules, state them explicitly


## ⚙️ Default Workflows

Every workspace includes these. They live in `_workspace/config/`.

### Setup (`_setup.md`)

Runs on first use. Must:
1. Verify folders exist (create missing ones)
2. Check requirements and report status
3. Walk the user through personalization
4. Save preferences to `_workspace/preferences/preferences.md`
5. Show available workflows
6. Log the session
7. Comment out the ACTIVATE line so setup doesn't repeat

### Logging (`_log.md`)

Runs after every workflow. Must:
1. Append to `_workspace/logs/LOG_yyyy_mm_dd.md` (one file per day)
2. Record which workflow ran, what happened, what files changed
3. Never log private content: summarize topics only

### Add Context (`_add-context.md`)

Lets users add reference material. Must:
1. Accept documents, images, pasted text, or URLs
2. Convert to clean markdown in `_workspace/context/`
3. Preserve content faithfully: no summarizing

### Add Workflow (`_add-workflow.md`)

Lets users create new workflows interactively. Must:
1. Guide the user through defining trigger, input, output, and boundaries
2. Write a complete workflow file to `_workspace/workflows/`
3. Register the workflow in CLAUDE.md so Claude can discover it

### Export Workspace (`_export-workspace.md`)

Packages the workspace for sharing or backup. Must:
1. Offer clean template (no personal data) or full export
2. Run a security scan before packaging
3. Generate a README for templates
4. Deliver a zip file


## 🛠️ Building Your Own

1. Copy this repo or create the structure from scratch
2. Write your CLAUDE.md following the spec above
3. Create your setup workflow in `_workspace/config/_setup.md`
4. Add workflow files to `_workspace/workflows/`
5. Zip and share


## 🔮 What's Next

This spec is a draft. We're working toward:
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
