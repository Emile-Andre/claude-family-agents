# Claude-Specific Template Sources

This file explains where to find pre-written Claude prompts you can copy into any `.mdc` agent file in this repo. Claude is designed by Anthropic and responds best to prompts written using XML-style tags (like `<role>`, `<instructions>`, `<limits>`), which is the format used throughout this project.

---

## 1. Anthropic Prompt Engineering Interactive Tutorial

**Link:** https://github.com/anthropics/prompt-eng-interactive-tutorial

**What it is:** The official Anthropic tutorial for writing effective Claude prompts. It is a Jupyter notebook you can open in Google Colab or locally.

**Best for:**
- Learning why Claude responds better to certain prompt structures
- Understanding how to write `<role>` and `<instructions>` sections that Claude takes seriously
- Beginners who want to understand prompt engineering before customizing agents

**How to use it for this repo:**
1. Open the notebook and read through the exercises.
2. Copy the prompt patterns from the exercises.
3. Paste them into the `<instructions>` section of your `.mdc` files.

---

## 2. Awesome Claude Prompts

**Link:** https://github.com/langgptai/awesome-claude-prompts

**What it is:** A community-maintained library of ready-made role-based prompts written specifically for Claude. Includes prompts for legal, writing, research, business, and personal productivity roles.

**Best for:**
- Finding a pre-written prompt for a specific job (e.g. editor, advisor, coach)
- Getting started quickly without writing prompts from scratch
- Inspiration for building your own custom agents

**How to use it for this repo:**
1. Browse the repository for a role that matches what you need.
2. Copy the prompt text.
3. Wrap it in `<role>` and `<instructions>` tags.
4. Paste it into a new `.mdc` file in `.cursor/rules/`.

---

## 3. Anthropic Official Prompt Library

**Link:** https://docs.anthropic.com/en/resources/prompt-library/library

**What it is:** Anthropic's own curated collection of tested prompts. These are written and maintained by Anthropic engineers and cover tasks like summarizing documents, drafting emails, and analyzing data.

**Best for:**
- High-quality, tested prompts that are guaranteed to work well with Claude
- Tasks like document review, summarization, and Q&A
- Users who want prompts backed by Anthropic directly

**How to use it for this repo:**
1. Visit the page and browse the categories.
2. Click on a prompt that matches your use case.
3. Copy the system prompt portion.
4. Add it to the `<role>` or `<instructions>` section of your `.mdc` file.

---

## 4. Awesome Cursor Rules

**Link:** https://github.com/patrickjs/awesome-cursorrules

**What it is:** A community library of `.cursorrules` and `.mdc` files for Cursor. While not all are Claude-specific, many work well with Claude through Cline.

**Best for:**
- Finding `.mdc`-formatted files you can use directly without reformatting
- Coding, writing, and productivity agent templates
- Users comfortable with the Cursor/Cline workflow

**How to use it for this repo:**
1. Browse the repository by category.
2. Download or copy the `.mdc` file for the role you want.
3. Drop it directly into `.cursor/rules/` in this project.
4. Rename it to match your agent name.

---

## 5. Claude Code System Prompts (Community)

**Link:** https://github.com/Piebald-AI/claude-code-system-prompts

**What it is:** A community repository that tracks and archives the internal system prompts Anthropic uses to instruct Claude Code itself. These are the actual instructions Anthropic gave to Claude's built-in agents.

**Best for:**
- Advanced users who want to understand how Anthropic engineers write agent instructions
- Borrowing language and structure from Anthropic's own internal prompts
- Building agents that behave predictably in a file-editing context

**How to use it for this repo:**
1. Browse the files to find the relevant agent type.
2. Read the prompt structure and tone.
3. Borrow the XML tag structure and instruction style for your own `.mdc` files.
4. Do not copy verbatim — adapt the language to match your family's use case.

---

## Tips for adapting any prompt into a .mdc file

1. Always add a `<role>` section that describes who the agent is in plain English.
2. Always add an `<instructions>` section with numbered steps.
3. Always add a `<limits>` section with things the agent should NOT do.
4. Keep the language simple. Avoid technical jargon unless your family is technical.
5. Test by opening Cline in Cursor and calling the agent by name.
6. If the agent does not behave as expected, read the instructions again and make them more specific.
