---
name: file-format-guide
description: Context and guide for file-format-guide customization
---

# VS Code Agent System — File Types Guide
## The 4 File Types at a Glance

VS Code uses four distinct `.md` file types, each with a different purpose and format.

| File Type | Extension | Folder | Purpose |
|---|---|---|---|
| Custom Instruction | `.instructions.md` | `.github/` or anywhere | Coding rules, standards always applied |
| Custom Agent | `.agent.md` | `.github/agents/` or `.claude/agents/` | Persistent persona with tools/handoffs |
| Agent Skill | `SKILL.md` (inside a folder) | `.github/skills/<skill-name>/` | Reusable portable capability with scripts |
| Prompt File | `.prompt.md` | `.github/prompts/` | Single-task slash command, invoked manually |

---

## `.instructions.md` — Custom Instructions

Automatically applied to all chat requests in the workspace. Used for coding standards, naming conventions, frameworks, etc.

### Example

```yaml
---
applyTo: "**/*.py"   # optional glob pattern; omit to apply to all files
---
```

```markdown
# Project Coding Standards
- Use snake_case for all Python variable names
- Always add type hints
- Prefer FastAPI over Flask
```

### YAML Frontmatter Keys

| Key | Required | Description |
|---|---|---|
| `applyTo` | No | Glob pattern to auto-apply (e.g. `"**/*.py"`, `"**"`) |

The body is plain Markdown instructions.

---

## `.agent.md` — Custom Agent

Creates a named agent persona with specific tools, model, and behavior.

**Stored in:**
- `.github/agents/` (VS Code format)
- `.claude/agents/` (Claude format)

### Example

```yaml
---
name: python-reviewer
description: Reviews Python code for quality, security, and PEP8 compliance
tools: ['search', 'read_file', 'list_dir']
model: Claude Sonnet 4.5 (copilot)
handoffs:
  - label: Fix Issues
    agent: implementation
    prompt: Now fix the issues found in the review.
    send: false
---
```

```markdown
# Python Code Reviewer

You are a strict Python code reviewer. Focus on:
- PEP8 style compliance
- Security vulnerabilities
- Proper error handling

Use #tool:read_file to read files before reviewing.
```

### YAML Frontmatter Keys

| Key | Required | Description |
|---|---|---|
| `name` | No | Display name; defaults to filename |
| `description` | No | Shown as placeholder in chat input |
| `tools` | No | Array of allowed tools |
| `model` | No | AI model to use |
| `agents` | No | Sub-agents this agent can invoke |
| `user-invocable` | No | Show in agents dropdown (default: `true`) |
| `disable-model-invocation` | No | Prevent auto-invoke as subagent |
| `handoffs` | No | Handoff buttons with label/agent/prompt |
| `hooks` | No | Agent-scoped hooks (Preview) |

> **Note:** Claude format uses comma-separated tools and supports `disallowedTools`.

---

## `SKILL.md` — Agent Skill

The most portable format — works across VS Code, Copilot CLI, and cloud agents.

### Required Folder Structure

```
.github/skills/
└── pdf-converter/
    ├── SKILL.md
    ├── convert-script.py
    └── examples/
```

### Example

```yaml
---
name: pdf-converter
description: Converts PDF files to Markdown format preserving tables. Use when asked to process or convert PDF documents.
argument-hint: "[pdf file path] [output options]"
user-invocable: true
disable-model-invocation: false
context: inline
---
```

```markdown
# PDF to Markdown Converter

## When to use this skill

Use when the user provides a PDF file that needs to be converted to Markdown.

## Steps to follow

1. Read the PDF using [convert script](./convert-script.py)
2. Preserve all tables as Markdown tables
3. Output as a `.md` file

## Examples

**Input:** `report.pdf`  
**Output:** `report.md` with `| col1 | col2 |` style tables
```

### YAML Frontmatter Keys

| Key | Required | Description |
|---|---|---|
| `name` | Yes | Must match folder name |
| `description` | Yes | What it does + when to use |
| `argument-hint` | No | Hint shown in chat |
| `user-invocable` | No | Enables `/skill-name` |
| `disable-model-invocation` | No | Prevent auto-loading |
| `context` | No | `inline` or `fork` |

---

## `.prompt.md` — Prompt File

Reusable slash command for a single, well-defined task.

### Example

```yaml
---
name: convert-pdf-tables
description: Converts a PDF file's tables into Markdown format
agent: agent
tools: ['read_file', 'create_file']
model: Claude Sonnet 4.5 (copilot)
---
```

```markdown
Convert the PDF at `${input:pdfPath:Enter the PDF file path}` to Markdown.

- Preserve all tables using Markdown table syntax `| col | col |`
- Use fenced code blocks for code sections
- Save output as `${input:outputPath:Enter output .md file path}`
```

### YAML Frontmatter Keys

| Key | Required | Description |
|---|---|---|
| `name` | No | Slash command name |
| `description` | No | Shown in `/` menu |
| `agent` | No | Execution mode (`ask`, `agent`, `plan`) |
| `model` | No | Model used |
| `tools` | No | Allowed tools |
| `argument-hint` | No | Input hint |

---

## Quick Tips

### Tool Reference Syntax

Use backtick-style references inside Markdown:

```
#tool:read_file
#tool:web/fetch
#tool:browser
```

Reference files with relative paths:

```
[my script](./script.py)
```

---

## Global Files

### `.github/copilot-instructions.md`

- Global instruction file
- No YAML frontmatter needed
- Applies to all chats

### `AGENTS.md`

- Used across multiple agent systems
- Supports nested rules in monorepos
- Ideal for workspace-wide governance
