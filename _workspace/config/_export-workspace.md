---
name: export-workspace
description: Export the workspace as a reusable zip template or a full backup
trigger: User wants to export, share, or package the workspace (e.g. "export my workspace", "create a template", "zip this workspace", "share my setup")
requirements: Bash (zip command)
---

# Workflow: Export Workspace

You help the user export their workspace as a zip file. The user chooses between a **clean template** (shareable, no personal data) or a **full export** (personal backup with everything).

---

# Before you begin

1. **Read preferences.** Check `/_workspace/preferences/preferences.md` for language preferences.
2. **Scan the workspace.** List all files and folders in the project root and `_workspace/` to understand what exists.

---

# Phase 1 — Choose export mode

Ask the user using `AskUserQuestion`:

> **How would you like to export?**
>
> 1. **Clean template** — A reusable workspace others can clone. Strips all personal data (logs, context files). Keeps workflows, config, and structure.
> 2. **Full export** — A personal backup with everything included.

**If clean template:** follow up with a second `AskUserQuestion`:

> **What should this workspace be called?**
> This name will appear in the README, CLAUDE.md, and zip filename.
> *(e.g. "Product Manager Toolkit", "Research Assistant", "Client Project Space")*

Also ask for a **one-line description** of what this workspace is for. These will be used to generate the README and update the CLAUDE.md header in the exported template.

---

# Phase 2 — Security scan

Before zipping anything, scan files that will be included for potentially sensitive content. This is especially important for files in `_workspace/context/` and `_workspace/preferences/`.

**Always check these locations:**

- `_workspace/context/*` — May contain contracts, personal documents, or confidential material. **Read each file** and flag anything that contains:
  - Personal identifiable information (addresses, birth dates, BSN/SSN, bank details)
  - Employment contracts, salary information
  - Credentials, API keys, tokens
  - Confidential business information
- `_workspace/preferences/*` — Check for personal details (name, role is fine — but flag if it contains anything beyond basic profile info)
- Root-level files — Check for `.env`, credentials, or config files with secrets

**Report findings to the user:**

> **Security check:**
> - ✅ [file] — clean
> - ⚠️ [file] — contains [type of sensitive data]. **Recommend excluding.**
>
> Want to proceed, or adjust what's included?

For **clean template** exports: recommend excluding any file with personal data by default. Let the user override.

For **full exports**: warn about sensitive files but include them unless the user says otherwise.

---

# Phase 3 — Build the zip

## Clean template export

**Generate a README.md** for the template (see below). This replaces any existing README.

**Update CLAUDE.md** in the staging copy:
- Replace the `Name:` and `Description:` values in the header with the workspace name and description the user provided.
- Ensure the setup activation line is **uncommented** so first-time setup triggers for the new user.

**Include:**
- `CLAUDE.md` (updated copy)
- `README.md` (generated)
- `LICENSE` (if exists)
- `_assets/` (full folder)
- `_workspace/config/` (all config files)
- `_workspace/workflows/` (all workflow files)
- `_workspace/preferences/` (include by default — these define the workspace personality and are useful as starting templates; but strip or generalize personal details like name/role if present)
- `.gitignore`

**Include as empty folders (create `.gitkeep` inside):**
- `_workspace/logs/`
- `_workspace/context/`

**Exclude:**
- `.git/`
- `.claude/`
- `.DS_Store` files
- `_workspace/logs/*` (content only — keep folder)
- `_workspace/context/*` (content only — keep folder)
- Any files flagged in the security scan
- Any root-level files that are not part of the template (user-created files in root)

**For root-level folders** (other than `_workspace/`, `_assets/`, `.git/`, `.claude/`):
- Include the folder structure but **not** the file contents — these are user data, not part of the reusable template
- Create `.gitkeep` files to preserve the folder structure

**Preferences handling:**
- Copy `_workspace/preferences/` files but **strip all user-provided values**. Keep the structure (headings, field labels) intact so the file serves as a blank template. For example, `preferences.md` should look like:
  ```markdown
  # User Preferences

  ## About
  - **Name:**
  - **Role:**

  ## General
  - **Primary use case:**
  - **Language:**

  ## Communication Style
  - **Detail level:**
  - **Tone:**

  ## Workflow-Specific Preferences
  ```
  ...and so on for all sections. The new user will fill these in during their own setup.

**README generation:**
Generate a `README.md` tailored to the exported workspace. Use this structure:

```markdown
# [Workspace Name]

[One-line description]

## What is this?

This is a **Claude Workspace** — a structured folder of workflows, preferences, and templates that Claude uses to assist you. Open this folder in your editor with Claude Code, and Claude knows how to help.

## Getting started

1. Open this folder in your editor
2. Start Claude Code
3. Say **"set up my space"** — Claude will walk you through a short configuration
4. You're ready to go!

## Workflows

| Workflow | What it does | Try saying... |
|----------|-------------|---------------|
[For each workflow in _workspace/workflows/, add a row with name, description from frontmatter, and trigger example]

## Requirements

[Copy from CLAUDE.md — hard and recommended requirements]

## Folder structure

| Folder | Purpose |
|--------|---------|
| `_workspace/config/` | System workflows (don't edit) |
| `_workspace/workflows/` | User-facing workflows |
| `_workspace/preferences/` | Your preferences (filled during setup) |
| `_workspace/context/` | Reference material and domain knowledge |
| `_workspace/logs/` | Session logs |
```

Populate the workflows table by reading the frontmatter (`name`, `description`, `trigger`) from each file in `_workspace/workflows/`. Only include user workflows, not system config workflows.

## Full export

**Include everything** in the project root, except:
- `.git/`
- `.claude/`
- `.DS_Store` files
- Any files the user explicitly excluded after the security scan

---

# Phase 4 — Create and deliver

1. **Determine filename:**
   - Clean template: `[workspace-name-slugified]_template_YYYY-MM-DD.zip` (e.g. `my-workspace_template_2026-03-24.zip`)
   - Full export: `workspace-export_YYYY-MM-DD.zip`

2. **Ask the user** where to save the zip using `AskUserQuestion`:
   > **Where should I save the zip?**
   > Default: `~/Desktop/[filename]`

3. **Create the zip** using the `zip` command via Bash. Use a temporary staging directory to assemble the clean template if needed.

   For clean template, the approach is:
   ```
   1. Create a temp directory
   2. Copy included files/folders
   3. Create .gitkeep files in empty folders
   4. Sanitize preferences (replace personal details with placeholders)
   5. Zip the temp directory
   6. Clean up temp directory
   ```

   For full export:
   ```
   1. Zip directly from the project root with exclusion flags
   ```

4. **Report the result:**
   > **Exported!**
   > - 📦 `[path/to/zip]`
   > - Size: [file size]
   > - Mode: [clean template / full export]
   > - Files included: [count]

5. **Show the user the zip file** using `present_files` if available.

6. **Show next steps message.** Tailor based on export mode:

   **For clean template:**
   > ## What's next?
   >
   > **Share it:**
   > - Send the zip to a colleague via Slack, email, or a shared drive
   > - Upload it to a GitHub repo as a template
   > - Drop it in a shared folder your team can access
   >
   > **They use it by:**
   > 1. Unzipping the file into a new folder
   > 2. Opening that folder in their editor
   > 3. Starting Claude Code — it will detect the workspace automatically
   > 4. Saying **"set up my space"** to personalize it
   >
   > **Optional:** If they need the same MCP integrations (e.g. Google Calendar), they'll need to configure those separately in their own `.claude/settings.json`.

   **For full export:**
   > ## What's next?
   >
   > **To restore this workspace:**
   > 1. Unzip the file into a folder
   > 2. Open it in your editor and start Claude Code
   > 3. Everything will be right where you left it
   >
   > **Tip:** Consider initializing a fresh git repo (`git init`) if you want version control on the restored copy.

---

# Quality Rules
- **Never include `.git/` or `.claude/`** — these are environment-specific and should never be exported.
- **Never include `.DS_Store` files** — these are OS artifacts.
- **Always run the security scan** — even for full exports, the user should know what sensitive data is being packaged.
- **Never invent content** — only package what actually exists in the workspace.
- **Preserve folder structure** — empty folders with `.gitkeep` are better than missing folders. The recipient should be able to use the template immediately.
- **Clean up after yourself** — remove any temporary staging directories after the zip is created.
