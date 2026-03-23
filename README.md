# Leverage Claude Workspace

A Workspace is a folder that turns Claude into a domain-specific assistant. No code, no build steps — just markdown files and folder conventions.

Workspaces are designed for Claude Cowork, a feature in the Claude Desktop app that lets you open a folder as a project. When Claude Cowork opens a folder, it reads the CLAUDE.md file and follows the instructions inside — that's all a Workspace is.

This repository is both the spec and a working example (a meeting notes assistant). Everything here demonstrates the patterns any Workspace should follow.


## How to Use a Workspace

1. Download the Workspace folder (or receive it as a zip)
2. Open Claude Desktop and go to Claude Cowork
3. Open the folder as a project
4. Claude reads CLAUDE.md, runs the setup workflow, and you're ready to go


## Structure

Every Workspace looks like this:

```
my-workspace/
  CLAUDE.md                            # Entry point. The only file Claude reads upfront.
  _workspace/
    config/                            # System workflows (not user-facing).
      _setup.md                        # Onboarding and configuration.
      _log.md                          # Session logging.
      _add-context.md                  # Document conversion.
    workflows/                         # User-facing workflows. One file per workflow.
      [workflow-name].md
    context/                           # User preferences. Gitignored.
    logs/                              # Session logs. Gitignored.
    sources/                           # Reference material. Gitignored. Recommended.
  [user-facing folders]/               # Workspace-specific. Gitignored.
```

Rules:
- `_workspace/` is reserved: don't use it for user content
- Files prefixed with `_` are system files
- All user data folders must be gitignored


## CLAUDE.md

The entry point. Claude reads this upfront and uses it to route user intent to workflow files. It must contain these sections, in order:

### Header

```markdown
# [Workspace Title]
- Name: [short name]
- Description: [what this workspace does]
- Version: [version number]
- Spec version: [spec version this workspace follows]
- Author: [who made it]
```

### Requirements

What the workspace needs. Two levels:

- Hard: Won't work without these. Setup should block or warn prominently.
- Recommended: Works without these, but some workflows will be limited.

If there are no hard requirements, say so explicitly.

### Folder Structure

Lists all folders, split into system folders (versioned, part of the template) and user data folders (gitignored, created during setup).

### Workflows

Maps user intent to workflow files. Every entry needs a name, a file path, and trigger examples. Split into:

- Default Workflows: Setup, Logging, Add Context. System workflows present in every workspace.
- User Workflows: What makes this workspace unique.

Must end with: `Before executing any workflow, you MUST read its instruction file in full.`

### Ground Rules

Must include at least these four:
- User data is sacred: never overwrite or delete without permission
- Never invent: only use what the user actually provided
- Always log sessions: run the logging workflow after every workflow
- Read files first: never edit a file you haven't read in this session

Authors can add more.

### Tone (recommended)

How Claude should communicate. Without it, Claude defaults to generic behavior.

### Do Not (recommended)

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

Every workspace includes these three. They live in `_workspace/config/`.

### Setup (`_setup.md`)

Runs on first use. Must:
1. Verify folders exist (create missing ones)
2. Check requirements and report status
3. Walk the user through personalization
4. Save preferences to `_workspace/context/preferences.md`
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
2. Convert to clean markdown in `_workspace/sources/`
3. Preserve content faithfully: no summarizing


## Building Your Own

1. Copy this repo or create the structure from scratch
2. Write your CLAUDE.md following the spec above
3. Create your setup workflow in `_workspace/config/_setup.md`
4. Add workflow files to `_workspace/workflows/`
5. Zip and share


## What's Next

This spec is a draft. We're working toward:

- A skill that generates Workspaces from a description
- A library of community Workspaces
- Native Claude Cowork integration


## License

[MIT](LICENSE)
