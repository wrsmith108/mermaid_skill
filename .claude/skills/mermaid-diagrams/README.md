# mermaid-diagrams

A Claude Code skill that makes Claude **always use mermaid** for structural diagrams and **never emit ASCII art**.

Author: Ryan Smith

## Why this exists

Many developers render mermaid fenced code blocks inline (e.g. via a VS Code extension, GitHub, or Obsidian). ASCII box-drawing diagrams look worse in those environments and don't add anything the rendered mermaid doesn't. This skill tells Claude to reach for mermaid by default.

## Installation

Source: https://github.com/wrsmith108/mermaid_skill

### From GitHub (recommended)

Clone the repo and copy the skill into place.

User-level (active in every Claude session):

```bash
git clone https://github.com/wrsmith108/mermaid_skill
cp -r mermaid_skill/.claude/skills/mermaid-diagrams ~/.claude/skills/
```

Project-level (active only in one repo):

```bash
git clone https://github.com/wrsmith108/mermaid_skill
mkdir -p .claude/skills
cp -r mermaid_skill/.claude/skills/mermaid-diagrams .claude/skills/
```

### From a local copy

If you already have the `mermaid-diagrams` directory on disk:

```bash
# User-level
cp -r mermaid-diagrams ~/.claude/skills/

# Project-level
mkdir -p .claude/skills && cp -r mermaid-diagrams .claude/skills/
```

Either way, the Claude Code harness auto-discovers skills at session start — no further setup.

## Triggers

The skill fires when the user asks for any of:

- "diagram", "flowchart", "architecture diagram"
- "sequence diagram", "state machine", "ER diagram", "class diagram"
- "gantt chart", "timeline"
- "draw …", "visualize …", "show the flow of …", "show the structure of …"

## What it does

- Forces Claude to emit mermaid fenced code blocks for structural diagrams
- Forbids ASCII box-drawing (`+---+`, `│`, `─`, `┌`, etc.) for diagrams
- Provides a selection guide for picking the right mermaid type
- Ships copy-pasteable examples for every supported type

## The one exception

File and directory tree listings (`tree`-style output and proposed layouts) are still allowed to use ASCII, since mermaid doesn't render them well. Everything else structural must be mermaid.

## Contents

| File | Purpose |
|---|---|
| `SKILL.md` | Core instructions Claude reads when the skill triggers |
| `references/diagram-types.md` | When to use each mermaid diagram type |
| `references/examples.md` | Copy-pasteable examples for each type |
| `CHANGELOG.md` | Version history |

## Scope

- **Public** — shareable and installable by others
- **Authored in-repo** at `.claude/skills/mermaid-diagrams/`
- **No hooks** — purely advisory, steers Claude's output via instructions
