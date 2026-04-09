# mermaid-diagrams

A private, project-scoped Claude Code skill that makes Claude **always use mermaid** for structural diagrams and **never emit ASCII art**.

## Why this exists

The developer of this project renders mermaid fenced code blocks inline via a VS Code extension. ASCII box-drawing diagrams look worse and don't add anything the rendered mermaid doesn't. This skill tells Claude to reach for mermaid by default.

## Installation

This skill is project-scoped and lives inside the repo at `.claude/skills/mermaid-diagrams/`. No install step — the Claude Code harness auto-discovers skills under `.claude/skills/` when a session starts.

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

- **Project-level** — only active in this repository
- **Private** — not published to any skill registry
- **No hooks** — purely advisory, steers Claude's output via instructions
