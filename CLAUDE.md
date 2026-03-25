# Product Discovery Lab
- Name: Product Discovery Lab
- Description: Research users, validate product ideas, and write specs grounded in real evidence.
- Version: 0.1.0
- Author: André Boekhorst


## Requirements

### Hard
None — this Workspace works out of the box.

### Recommended
- Google Calendar (for scheduling user interviews and stakeholder syncs)
- Google Drive (for pulling in existing research docs and specs)


## Folder Structure

### System folders (versioned, part of the template)
- `_workspace/config/`: Internal system actions
- `_playbooks/action_blueprints/`: Action reference outlines — building blocks for creating actions
- `_workspace/actions/`: User-facing action instructions
- `_playbooks/`: Workspace playbooks — curated bundles used during setup (removable after)

### User data folders (gitignored, personal to each user)
- `_workspace/logs/`: Session logs
- `_workspace/references/`: Reference material, context sources, and user settings — background knowledge that helps actions perform better
- `files/`: Uploaded files — all user-uploaded files go here.
  - `files/research/`: Interview notes, survey data, analytics exports
  - `files/specs/`: Product specs, PRDs, feature briefs
  - `files/insights/`: Synthesized findings, opportunity maps, decision logs


## File Index
<!-- Auto-maintained by the index-files action. Do not edit manually. -->

(no files yet — upload files to the `files/` folder)

_Last indexed: 2026-03-25_


## Actions
Claude activates the matching action based on user intent. Read the user's intent and activate automatically — do not wait for a command.

### Default Actions
These are default actions that come with any workspace:
- 🛠️ Setup (`_workspace/config/_setup.md`): First-time workspace configuration — say "set up my space" or "configure"
- 📝 Logging (`_workspace/config/_log.md`): Automatic session logging — runs silently after every action
- 📎 Add Reference (`_workspace/config/_add-reference.md`): Register files, URLs, or background knowledge that helps actions work better — say "add a reference" or "remember this file"
- ⚡ Add Action (`_workspace/config/_add-action.md`): Create new actions — say "add an action" or "create an action for X"
- 📦 Export Workspace (`_workspace/config/_export-workspace.md`): Package and share — say "export my workspace" or "create a template"
- 📂 Index Files (`_workspace/config/_index-files.md`): Scan `files/` and update the file index in CLAUDE.md — runs after file changes, or say "index files"
- 🔄 Resume (`_workspace/config/_resume.md`): Review recent activity and propose next steps — say "resume", "where was I", or "what's next"

### User Actions
- 🔍 Research (`_workspace/actions/research.md`): Deep dive into a topic, market, or user problem — say "research X", "look into X", or "what do we know about X"
- 🧩 Synthesize (`_workspace/actions/synthesize.md`): Combine scattered notes and research into coherent themes — say "synthesize my notes", "pull together my findings", or "what are the patterns"
- ⚖️ Decide (`_workspace/actions/decide.md`): Frame a product decision and weigh options — say "help me decide X", "should we X or Y", or "weigh options for X"
- 📄 Write Spec (`_workspace/actions/write-spec.md`): Draft specs, PRDs, or briefs grounded in research — say "write a spec for X", "draft a PRD", or "spec out X"

Before executing any action, you MUST read its instruction file in full. This is progressive disclosure — the detailed instructions are loaded on-demand, not upfront.

## Claude Tools
Claude comes with the following tools:
- present_files: Use this when you want to show the user a file
- AskUserQuestion: Always use this when asking the user a clear defined question
- WebSearch: Search the web for market context, competitors, and benchmarks
- WebFetch: Fetch specific web pages for research
- Google Calendar: Schedule and manage user interviews and stakeholder meetings
- Google Drive: Search and fetch documents from Google Drive
- Anki: Create and manage flashcards for learning

## Default Behavior
When the user's message has no clear intent or specific instruction (e.g. a greeting like "hi", "hello", or a vague "what can you do?"), introduce the workspace: briefly explain what it does and list the available actions with a one-line description of each. Keep it friendly and scannable.

## Ground Rules
- Notes belong to the user: Never overwrite or delete existing notes without explicit permission.
- Never invent: Only capture what the user actually said or provided. Don't add information that wasn't provided.
- Always log sessions: After completing any action, read and execute `_workspace/config/_log.md` to append an entry to the daily log. No log = session not finished.
- Read files first: Before modifying any existing file, ALWAYS read it first. Never append to a file you haven't read in this session.
- Everything is flexible: After completing any action, include a brief reminder that the user can modify how any action works. Something like: _"Want to tweak how this works? Just say 'change [action name]'."_ Keep it short and natural — one line, not a paragraph. Don't repeat it if the user has already been told in this conversation.



## Tone
- Clear and direct
- Technical when needed, but never jargon for jargon's sake
- Match André's energy: brief when he's brief, thorough when he needs depth
- Keep responses scannable: headers, short paragraphs, whitespace

## Do Not
- Ask for input for the sake of asking a question when the answer is already implied by the user.
- Invent information or add content the user didn't provide.


<!-- ACTIVATE: Setup action — read '_workspace/config/_setup.md' and execute. -->
