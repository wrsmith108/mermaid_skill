# mermaid_skill

Home of the **`mermaid-diagrams`** Claude Code skill — a skill that steers Claude to always emit mermaid fenced code blocks for structural diagrams and never fall back to ASCII art.

**Author:** Ryan Smith
**License:** see repository
**Latest version:** `1.1.1`

## What's in here

```
.claude/skills/mermaid-diagrams/
├── SKILL.md              # Core instructions Claude reads when the skill triggers
├── README.md             # Full skill documentation
├── CHANGELOG.md          # Version history
└── references/
    ├── diagram-types.md  # When to use each mermaid type
    └── examples.md       # Copy-pasteable examples
```

The full skill documentation lives at [`.claude/skills/mermaid-diagrams/README.md`](./.claude/skills/mermaid-diagrams/README.md).

## Quick install

User-level (active in every Claude Code session):

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

The Claude Code harness auto-discovers skills at session start — no further setup.

## What the skill does

- Forces Claude to emit mermaid fenced code blocks for structural diagrams
- Forbids ASCII box-drawing (`+---+`, `│`, `─`, `┌`, etc.) for diagrams
- Ships a diagram-type selection guide (`flowchart`, `sequenceDiagram`, `stateDiagram-v2`, `erDiagram`, `classDiagram`, `gantt`, `gitGraph`)
- Ships copy-pasteable examples for every supported type
- Allows ASCII `tree`-style output for filesystem layouts (the only exception)

## Triggers

The skill fires when the user asks for any of:

- "diagram", "flowchart", "architecture diagram"
- "sequence diagram", "state machine", "ER diagram", "class diagram"
- "gantt chart", "timeline"
- "draw …", "visualize …", "show the flow of …", "show the structure of …"

See the [skill README](./.claude/skills/mermaid-diagrams/README.md) for full details.
