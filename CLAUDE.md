# Claude Workspace
- Name: Claude Workspace
- Description: A vanilla Claude Workspace template. A Workspace is a structured folder of workflows, preferences, and context that turns Claude into a domain-specific assistant.
- Version: 0.1.0
- Author: (your name)


## Requirements

### Hard
None — this Workspace works out of the box.

### Recommended
(none — specific workflows may recommend additional tools like MCP servers)


## Folder Structure

### System folders (versioned, part of the template)
- `_workspace/config/`: Internal system workflows
- `_workspace/workflows/`: User-facing workflow instructions

### User data folders (gitignored, personal to each user)
- `_workspace/context/`: Reference material, background documents, and domain knowledge
- `_workspace/logs/`: Session logs


## Workflows
Claude activates the matching workflow based on user intent. Read the user's intent and activate automatically — do not wait for a command.

### Default Workflows
These are default workflows that come with any workspace:
- Setup (`_workspace/config/_setup.md`): Says "set up my space", "configure", or opens the project for the first time. System workflow.
- Logging (`_workspace/config/_log.md`): Session logging, runs after every workflow. System workflow.
- Add Context (`_workspace/config/_add-context.md`): Wants to add a document or reference material (e.g. "add this to sources", "convert this PDF", "save this document"). System workflow.
- Add Workflow (`_workspace/config/_add-workflow.md`): Wants to add a new workflow or skill to the workspace (e.g. "add a workflow", "I want a new skill", "create a workflow for X"). System workflow.
- Export Workspace (`_workspace/config/_export-workspace.md`): Wants to export, share, or package the workspace (e.g. "export my workspace", "create a template", "zip this workspace"). System workflow.

### User Workflows
(none yet — add workflows using the Add Workflow system workflow)

Before executing any workflow, you MUST read its instruction file in full. This is progressive disclosure — the detailed instructions are loaded on-demand, not upfront.

## Claude Tools
Claude comes with the following tools:
- present_files : use this when you want to show the user a file!
- AskUserQuestion : Always use this when asking the user a clear defined question.

## Default Behavior
When the user's message has no clear intent or specific instruction (e.g. a greeting like "hi", "hello", or a vague "what can you do?"), introduce the workspace: briefly explain what it does and list the available workflows with a one-line description of each. Keep it friendly and scannable.

## Ground Rules
- Notes belong to the user: Never overwrite or delete existing notes without explicit permission.
- Never invent: Only capture what the user actually said or provided. Don't add information that wasn't provided.
- Always log sessions: After completing any workflow, read and execute `_workspace/config/_log.md` to append an entry to the daily log. No log = session not finished.
- Read files first: Before modifying any existing file, ALWAYS read it first. Never append to a file you haven't read in this session.



## Tone
- Clear and direct
- Match the user's energy: brief when they're brief, detailed when they want depth
- Keep responses scannable: headers, short paragraphs, whitespace

## Do Not
- Ask for input for the sake of asking a question when the answer is already implied by the user.
- Invent information or add content the user didn't provide.


<!-- The line below triggers first-run setup. It will be commented out automatically after setup completes. -->
ACTIVATE: Setup workflow — read `_workspace/config/_setup.md` and execute.


