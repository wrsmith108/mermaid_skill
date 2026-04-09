# Plan: `mermaid-diagrams` skill

## Goal
Ensure Claude **always uses mermaid fenced code blocks** when producing diagrams, and **never emits ASCII art diagrams**, because the user renders mermaid inline via a VS Code extension.

## Approach
Build this as a **skill** (SKILL.md). Skills are model-readable, compose with other skills, and load on trigger. No hooks, no extra moving parts.

## Decisions

- **Scope:** project-level — installed at `.claude/skills/mermaid-diagrams/` inside this repo.
- **Distribution:** private skill, not published.
- **File-tree exception:** allowed. `tree`-style ASCII directory listings are fine since mermaid doesn't render them well. Everything else structural must be mermaid.

## Proposed skill structure

```
.claude/skills/mermaid-diagrams/
├── SKILL.md              # triggers, rules, examples
├── README.md             # human-facing
└── references/
    ├── diagram-types.md  # which mermaid type to pick
    └── examples.md       # flowchart, sequence, ER, state, gantt, class
```

## `SKILL.md` contents (summary)

- **Triggers:** "diagram", "flowchart", "architecture diagram", "sequence", "draw", "visualize", "show the flow", "show the structure"
- **Core rule:** When a diagram would help, emit a ` ```mermaid ` fenced block. Never use `+---+`, `│`, `└`, `├`, or ASCII tree drawings for structural diagrams.
- **Diagram-type selection guide:**
  - Process/flow → `flowchart`
  - Interaction between actors → `sequenceDiagram`
  - State machine → `stateDiagram-v2`
  - Data model → `erDiagram`
  - Class hierarchy → `classDiagram`
  - Timeline/schedule → `gantt`
  - Dependency tree → `flowchart TD`
- **Anti-patterns** (with examples of what NOT to do): ASCII boxes, indented bullet "trees" masquerading as diagrams, Unicode box-drawing.
- **Exception:** file/directory trees (`tree` output) are allowed since mermaid doesn't render them well — but note this as the only exception.

## Installation

1. `.claude/skills/mermaid-diagrams/` gets created in this repo with the files above
2. Skill auto-discovered by the Claude Code harness on next session
3. Feedback memory already saved at `memory/feedback_diagrams.md` reinforces the rule even when the skill hasn't been triggered yet
