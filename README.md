# claude-family-agents

5 specialized Claude agents for Cursor + Cline. Use your existing **Claude Pro subscription** — no separate API key or per-token billing required.

---

## What is in this repo

| File | Purpose |
|------|---------|
| `.cursor/rules/legal-reviewer.mdc` | Reviews documents and flags legal risk |
| `.cursor/rules/document-drafter.mdc` | Writes and polishes letters, agreements, summaries |
| `.cursor/rules/research-assistant.mdc` | Gathers facts, compares options, organizes findings |
| `.cursor/rules/file-organizer.mdc` | Renames and restructures project files and folders |
| `.cursor/rules/planner-coordinator.mdc` | Breaks tasks into steps and routes to the right agent |
| `templates/agent-template.mdc` | Blank template for creating your own agents |
| `docs/template-sources.md` | Links to Claude-specific prompt libraries |

---

## How this works (plain English)

- **Claude Code** is a tool made by Anthropic that lets Claude read and edit files on your computer. It is separate from the Claude desktop app.
- **Cursor** is a code editor (like Microsoft Word but for files and folders). It shows your GitHub files in a sidebar.
- **Cline** is a free plugin you install inside Cursor. It adds a chat panel on the side so you can talk to Claude directly about your files.
- The `.mdc` files in this repo are plain text instructions that tell Claude which role to play. You call them by typing `@agent-name` in the Cline chat.

---

## Full setup guide (step by step)

### Step 1 — Install GitHub Desktop

1. Go to https://desktop.github.com and download GitHub Desktop.
2. Install it and sign into your GitHub account.
3. This lets you manage files between your computer and GitHub without using a terminal.

### Step 2 — Clone this repo to your computer

1. Open GitHub Desktop.
2. Click **File** in the top menu, then click **Clone repository**.
3. Click the **URL** tab.
4. Paste this URL: `https://github.com/Emile-Andre/claude-family-agents`
5. Choose a folder on your computer where you want the files saved.
6. Click **Clone**.
7. You now have all the agent files on your computer.

### Step 3 — Install Cursor

1. Go to https://cursor.com and download Cursor for your operating system (Mac or Windows).
2. Install it like any normal app.
3. Open Cursor.
4. Click **File > Open Folder** and select the `claude-family-agents` folder you just cloned.
5. You will see all the repo files appear in the left sidebar.

### Step 4 — Install the Cline extension inside Cursor

1. In Cursor, look for the **Extensions** icon on the left sidebar (it looks like 4 small squares).
2. Click it to open the Extensions panel.
3. In the search bar at the top, type **Cline**.
4. Click **Install** on the Cline extension.
5. After installing, you will see a new Cline icon appear in the left sidebar.
6. Click it to open the Cline chat panel.

Cline GitHub page for reference: https://github.com/cline/cline

### Step 5 — Install Claude Code on your computer

1. You need to have **Node.js** installed first. Go to https://nodejs.org and download the LTS version. Install it.
2. Open a terminal:
   - **Mac:** Press `Cmd + Space`, type `Terminal`, press Enter.
   - **Windows:** Press `Windows key`, type `cmd`, press Enter.
3. Type this command and press Enter:
   ```
   npm install -g @anthropic-ai/claude-code
   ```
4. After it installs, type this command to log in:
   ```
   claude
   ```
5. It will open a browser window asking you to sign in with your **Claude Pro account** (the same account you pay $20/month for).
6. Sign in and approve the connection.
7. Claude Code is now authenticated and linked to your Pro subscription.

Official Claude Code docs: https://docs.anthropic.com/en/docs/claude-code/overview

### Step 6 — Connect Cline to Claude Code

1. In Cursor, open the Cline chat panel.
2. Click the **Settings** gear icon inside Cline.
3. For the **API Provider**, look for an option that says **Claude Code** or **Use local Claude Code CLI**.
4. Select that option. Do NOT paste an API key — this routes through your Pro subscription instead.
5. Click **Save**.
6. Restart Cursor.

> Note: Cline settings change as new versions are released. If you do not see a Claude Code option, check the Cline discussions page for the latest instructions: https://github.com/cline/cline/discussions

### Step 7 — Understand the agent files

Open the `.cursor/rules/` folder in Cursor's sidebar. You will see 5 files:

- `legal-reviewer.mdc` — flags risks, missing clauses, and issues in documents
- `document-drafter.mdc` — writes clean, professional documents from rough notes
- `research-assistant.mdc` — researches topics and compares options clearly
- `file-organizer.mdc` — cleans up folders and suggests consistent naming
- `planner-coordinator.mdc` — figures out which agent to use and makes a step-by-step plan

Each file is written in plain English. You can open any of them and edit the instructions to match your family's preferences.

### Step 8 — Use an agent

1. Open the Cline chat panel in Cursor.
2. Drag a file from the sidebar into the chat, or just describe what you need.
3. Start your message by mentioning the agent you want. Examples:

| What you want to do | What to type |
|---------------------|--------------|
| Check a contract for problems | `@legal-reviewer please review this agreement and flag anything risky` |
| Write a professional letter | `@document-drafter draft a formal letter declining this service` |
| Compare two internet providers | `@research-assistant compare these two plans and tell me which is better` |
| Clean up a messy folder | `@file-organizer suggest a clean naming system for these files` |
| Not sure where to start | `@planner-coordinator I need to review this contract and then send a response` |

### Step 9 — Customize agents for your family

Open any `.mdc` file in Cursor and edit the instructions in plain English. Good things to add:

- Your preferred tone (e.g. "always be friendly but professional")
- Standard sections you always want in documents
- A rule like "always ask before saving or deleting any file"
- Your family's last name or address for document templates

After editing, save the file (Cmd+S on Mac, Ctrl+S on Windows).

### Step 10 — Save your changes back to GitHub

1. Open GitHub Desktop.
2. You will see your changed files listed on the left.
3. At the bottom left, type a short description like `updated legal agent`.
4. Click **Commit to main**.
5. Click **Push origin** at the top.
6. Your changes are now saved to GitHub and backed up.

---

## Safety rules for non-technical users

- **Never let an agent delete files without asking you first.** The agents in this repo are set to always confirm before deleting.
- **The legal agent is not a lawyer.** It helps you spot issues and draft documents but cannot give official legal advice.
- **Keep important files in GitHub.** If an agent makes a mistake, GitHub lets you undo any change by reverting to a previous version.
- **Do not share your Claude login with anyone.** Your Pro subscription is personal.

---

## Template sources for Claude-specific prompts

These are the best places to find pre-written Claude prompts you can paste into any `.mdc` file:

| Source | Link | Best for |
|--------|------|----------|
| Anthropic Prompt Engineering Tutorial | https://github.com/anthropics/prompt-eng-interactive-tutorial | Learning how Claude thinks |
| Awesome Claude Prompts | https://github.com/langgptai/awesome-claude-prompts | Ready-made role templates |
| Awesome Cursor Rules | https://github.com/patrickjs/awesome-cursorrules | Cursor-specific `.mdc` templates |
| Claude Code System Prompts (community) | https://github.com/Piebald-AI/claude-code-system-prompts | How Anthropic instructs its own agents |
| Anthropic Official Prompt Library | https://docs.anthropic.com/en/resources/prompt-library/library | Anthropic-tested templates |

See `docs/template-sources.md` for more detail on how to use each one.

---

## How to add a new agent

1. Open the `templates/agent-template.mdc` file.
2. Copy its contents.
3. Create a new file inside `.cursor/rules/` — for example `tax-helper.mdc`.
4. Paste the template contents and fill in the role, instructions, and boundaries.
5. Save, commit, and push via GitHub Desktop.
6. Your new agent is ready to use immediately in Cline.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Cline does not respond | Make sure you ran `claude` in the terminal and logged in first |
| Agent does not follow the rules | Make sure the `.mdc` file is saved and Cursor has been restarted |
| Changes not showing in GitHub | Open GitHub Desktop and click Push origin |
| Claude asks for an API key | Select the Claude Code provider in Cline settings, not the Anthropic API option |
| Node.js not found | Re-install Node.js from https://nodejs.org and restart your terminal |

---

## Questions?

Open an Issue on this repo and describe your problem. Include what step you are on and what happened.
