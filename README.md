# claude-family-agents

5 specialized Claude agents for Cursor + Claude Code. Use your existing **Claude Pro subscription** — no separate API key or per-token billing required.

> **Note (April 2026):** Cline, Roo Code, OpenClaw, and similar third-party tools were blocked by Anthropic from using Claude Pro/Max subscriptions as of early April 2026. This repo has been updated to use **native Claude Code** instead, which is the official, supported workflow that Anthropic built and continues to maintain.

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

- **Claude Code** is a tool made by Anthropic that lets Claude read and edit files on your computer directly. It is the official, supported way to use Claude with local files. It is separate from the Claude desktop app (which is just a chat window).
- **Cursor** is a code editor (like Microsoft Word but for files and folders). It shows your GitHub files in a sidebar and has a built-in chat panel called the **Cursor Chat**.
- The `.mdc` files in this repo are plain text instructions that tell Claude which role to play when you open a chat inside Cursor.
- You do **not** need Cline, Roo Code, or any third-party extension. Everything runs through Claude Code natively.

---

## The workflow at a glance

```
Your Claude Pro account
        |
  Claude Code CLI  (installed once, logs in with your Pro account)
        |
   Cursor Editor  (opens your GitHub folder, has built-in chat)
        |
   .mdc rule files  (tell Claude which agent to be)
```

When you open Cursor's built-in chat and Claude Code is authenticated, Cursor talks directly to Claude through the official Claude Code channel. No third-party tools involved.

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

### Step 4 — Install Node.js (required for Claude Code)

1. Go to https://nodejs.org and download the **LTS** version.
2. Install it like any normal app. This only needs to be done once.
3. You can verify it worked by opening a terminal and typing `node --version`. If it shows a number, you are done.

   - **Mac:** Press `Cmd + Space`, type `Terminal`, press Enter.
   - **Windows:** Press the Windows key, type `cmd`, press Enter.

### Step 5 — Install Claude Code

1. Open a terminal (see Step 4 for how to open one).
2. Type this command and press Enter:
   ```
   npm install -g @anthropic-ai/claude-code
   ```
3. Wait for it to finish. You will see text scrolling. That is normal.
4. Once it finishes, type this and press Enter:
   ```
   claude
   ```
5. A browser window will open asking you to sign into your **Claude Pro account** (the same $20/month account you already pay for).
6. Sign in and approve the connection.
7. You will see a confirmation in the terminal. Claude Code is now linked to your Pro subscription.

Official Claude Code docs: https://docs.anthropic.com/en/docs/claude-code/overview

> **Why this works without API billing:** Claude Code is Anthropic's own CLI tool. When you log in with your Claude Pro account, it uses your subscription just like the Claude website does. Anthropic explicitly supports this. Third-party tools like Cline were blocked because they used consumer subscription credentials in ways Anthropic never intended.

### Step 6 — Open Claude Code inside the project folder

1. In Cursor, open the built-in terminal by pressing `` Ctrl + ` `` (the backtick key, top-left of keyboard).
2. Type this command to navigate into the project folder:
   ```
   cd claude-family-agents
   ```
3. Now type:
   ```
   claude
   ```
4. Claude Code will start running inside your project folder. You will see a `>` prompt.
5. You are now talking directly to Claude with full access to all the files in your project.

### Step 7 — Use an agent by loading its rule file

This is how you activate a specific agent. Instead of a Cline `@mention`, you simply tell Claude Code to read the rule file for the agent you want:

**Example — using the legal reviewer:**
```
> Read .cursor/rules/legal-reviewer.mdc and then review the file contract.pdf
```

**Example — using the document drafter:**
```
> Read .cursor/rules/document-drafter.mdc and draft a formal complaint letter about my landlord not fixing the heating
```

**Example — using the planner:**
```
> Read .cursor/rules/planner-coordinator.mdc and help me figure out what to do with this situation: [describe your task]
```

Claude will read the rule file, take on that agent's role and instructions, then help you with your task.

### Step 8 — Shortcut: Use the Cursor built-in chat with rules

You can also use Cursor's built-in chat panel (not a third-party extension) with these rule files:

1. In Cursor, press `Ctrl + L` (or `Cmd + L` on Mac) to open the Chat panel.
2. At the top of the chat, click **+ Add context** or drag the `.mdc` file from the sidebar directly into the chat box.
3. Type your request. Cursor will send the rule file as context to Claude automatically.
4. This does require a **Cursor Pro** subscription ($20/month) for full Claude access, separate from Claude Pro.

> If you do not want to pay for Cursor Pro, use the Claude Code terminal method in Step 6 and 7 instead. That only requires your existing Claude Pro subscription.

### Step 9 — Understand the agent files

Open the `.cursor/rules/` folder in Cursor's sidebar. You will see 5 files:

- `legal-reviewer.mdc` — flags risks, missing clauses, and issues in documents
- `document-drafter.mdc` — writes clean, professional documents from rough notes
- `research-assistant.mdc` — researches topics and compares options clearly
- `file-organizer.mdc` — cleans up folders and suggests consistent naming
- `planner-coordinator.mdc` — figures out which agent to use and makes a step-by-step plan

Each file is written in plain English. You can open any of them in Cursor and edit the instructions to match your preferences.

### Step 10 — Day-to-day usage (the simple routine)

Once everything is set up, your family's daily workflow is:

1. Open Cursor.
2. Press `` Ctrl + ` `` to open the terminal inside Cursor.
3. Type `claude` and press Enter.
4. Tell Claude which agent to use and what you need:
   ```
   > Read .cursor/rules/legal-reviewer.mdc and review this agreement: [paste text or drag file]
   ```
5. Claude responds directly in the terminal with its analysis, draft, or plan.
6. When done, type `exit` to close Claude Code.

### Step 11 — Customize agents for your family

Open any `.mdc` file in Cursor and edit the instructions in plain English. Good things to add:

- Your preferred tone (e.g. "always be friendly but professional")
- Standard sections you always want in documents
- A rule like "always ask before saving or deleting any file"
- Your family's common document types or naming preferences

After editing, save the file with `Cmd+S` (Mac) or `Ctrl+S` (Windows).

### Step 12 — Save your changes back to GitHub

1. Open GitHub Desktop.
2. You will see your changed files listed on the left.
3. At the bottom left, type a short description like `updated legal agent`.
4. Click **Commit to main**.
5. Click **Push origin** at the top.
6. Your changes are now saved to GitHub and backed up.

---

## Why not Cline, Roo Code, or OpenClaw?

As of April 4, 2026, Anthropic blocked these tools from using Claude Pro and Max subscriptions. The reason is that these tools were making API-scale requests using consumer subscription credentials, which violates Anthropic's Terms of Service and was costing Anthropic significant money. Users of these tools now need to either:

- Pay Anthropic API rates separately (per token, not a flat subscription), OR
- Use Claude Code, which is the official supported workflow

This repo uses **Claude Code** because it is the only method Anthropic officially supports for local file access with a Pro subscription. It was built by Anthropic, is maintained by Anthropic, and is not at risk of being blocked.

Sources:
- https://wotai.co/blog/woterclip-wont-get-blocked-anthropic
- https://techcrunch.com/2026/04/10/anthropic-temporarily-banned-openclaws-creator-from-accessing-claude/

---

## Safety rules for non-technical users

- **Never let an agent delete files without asking you first.** The agents in this repo are set to always confirm before deleting.
- **The legal agent is not a lawyer.** It helps you spot issues and draft documents but cannot give official legal advice.
- **Keep important files in GitHub.** If an agent makes a mistake, GitHub lets you undo any change by reverting to a previous version.
- **Do not share your Claude login with anyone.** Your Pro subscription is personal.
- **Only run `claude` inside your project folder.** Do not run it in sensitive system folders.

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
6. Use it by telling Claude Code: `Read .cursor/rules/tax-helper.mdc and [your task]`

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| `claude` command not found | Re-run `npm install -g @anthropic-ai/claude-code` and restart your terminal |
| Claude asks me to log in again | Run `claude` and sign in with your Claude Pro account in the browser |
| Agent does not follow the rules | Make sure you told Claude to read the `.mdc` file first in your message |
| Changes not showing in GitHub | Open GitHub Desktop and click Push origin |
| Node.js not found | Re-install Node.js from https://nodejs.org and restart your terminal |
| Cursor chat uses credits | Use the terminal method instead (`Ctrl + ` backtick, then `claude`) to avoid Cursor credit usage |

---

## Questions?

Open an Issue on this repo and describe your problem. Include what step you are on and what happened.
