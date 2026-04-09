# Mermaid diagram type selection guide

Pick the type that matches the *intent*, not the one that looks closest to what the user drew in chat.

## flowchart

Use for processes, pipelines, decision trees, dependency graphs, or anything where boxes point at other boxes.

- `flowchart LR` — left-to-right. Default for most flows; reads like prose.
- `flowchart TD` — top-down. Better for hierarchies, decision trees, dependency trees.
- `flowchart BT` / `RL` — rare; only when the natural reading is bottom-up or right-to-left.

Node shapes carry meaning — use them:

- `A[Rectangle]` — a step or component
- `A(Rounded)` — a softer step or terminator
- `A([Stadium])` — a start/end node
- `A[[Subroutine]]` — a reusable process
- `A[(Database)]` — a datastore
- `A{Decision}` — a decision/branch
- `A((Circle))` — a connector or junction

## sequenceDiagram

Use when the story is **who talks to whom, in what order**. Actors on top, time flowing downward.

Good fits: auth flows, API request/response sequences, webhook delivery, message-passing between services.

Bad fit: static architecture — use `flowchart` instead.

## stateDiagram-v2

Use for state machines and lifecycles — anything with a finite set of states and transitions between them.

Good fits: order status, deployment lifecycle, connection state, UI modal states.

Always use the `-v2` variant — the old `stateDiagram` is deprecated.

## erDiagram

Use for data models: entities, their attributes, and the cardinality of relationships between them.

Good fits: database schema overviews, "how do these tables relate" questions.

Bad fit: object-oriented class hierarchies — use `classDiagram`.

## classDiagram

Use for class hierarchies, interfaces, inheritance, and composition in OO code.

Good fits: "show me how these classes relate", "diagram this type hierarchy".

Bad fit: data models for a relational database — use `erDiagram`.

## gantt

Use for schedules, timelines, project plans with start/end dates.

Good fits: roadmaps, sprint plans, release timelines.

Bad fit: pure ordering without time — use `flowchart` instead.

## gitGraph

Use for git branching diagrams: branches, merges, commits.

Good fits: explaining a branching strategy, showing a merge/rebase sequence.

## Decision rule

If you find yourself reaching for `flowchart` for everything, stop and ask:

- Does time or ordering matter between actors? → `sequenceDiagram`
- Are the boxes really *states* of one thing? → `stateDiagram-v2`
- Are they database tables? → `erDiagram`
- Are they classes with inheritance? → `classDiagram`
- Does it have calendar dates? → `gantt`

Otherwise, `flowchart` is the right answer.
