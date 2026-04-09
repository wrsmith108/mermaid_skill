# Mermaid examples

Copy-pasteable starting points for each supported diagram type. Adapt labels and shapes to the actual subject.

## flowchart (LR)

```mermaid
flowchart LR
    User([User]) --> API[API Gateway]
    API --> Auth{Authenticated?}
    Auth -->|Yes| Service[Service]
    Auth -->|No| Reject[401 Response]
    Service --> DB[(Database)]
    Service --> Cache[(Cache)]
```

## flowchart (TD) — for hierarchies

```mermaid
flowchart TD
    Root[Root Module] --> A[Component A]
    Root --> B[Component B]
    A --> A1[Child A1]
    A --> A2[Child A2]
    B --> B1[Child B1]
```

## sequenceDiagram

```mermaid
sequenceDiagram
    participant C as Client
    participant A as API
    participant D as Database

    C->>A: POST /login
    A->>D: SELECT user
    D-->>A: user row
    A->>A: verify password
    A-->>C: 200 + token
    Note over C,A: Token valid for 1h
```

## stateDiagram-v2

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> Submitted: submit
    Submitted --> Approved: approve
    Submitted --> Rejected: reject
    Rejected --> Draft: revise
    Approved --> [*]
```

## erDiagram

```mermaid
erDiagram
    USER ||--o{ ORDER : places
    ORDER ||--|{ LINE_ITEM : contains
    PRODUCT ||--o{ LINE_ITEM : "appears in"

    USER {
        uuid id PK
        string email
        string name
    }
    ORDER {
        uuid id PK
        uuid user_id FK
        timestamp created_at
    }
    LINE_ITEM {
        uuid id PK
        uuid order_id FK
        uuid product_id FK
        int quantity
    }
```

## classDiagram

```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +makeSound() void
    }
    class Dog {
        +String breed
        +fetch() void
    }
    class Cat {
        +boolean indoor
        +purr() void
    }
    Animal <|-- Dog
    Animal <|-- Cat
```

## gantt

```mermaid
gantt
    title Release Plan
    dateFormat  YYYY-MM-DD
    section Design
    Wireframes       :done,    des1, 2026-03-01, 5d
    Visual design    :active,  des2, 2026-03-06, 7d
    section Build
    Frontend         :         dev1, after des2, 10d
    Backend          :         dev2, 2026-03-10, 12d
    section Launch
    QA               :         qa,   after dev1, 5d
    Release          :milestone, rel, after qa, 0d
```

## gitGraph

```mermaid
gitGraph
    commit id: "init"
    branch feature
    checkout feature
    commit id: "wip"
    commit id: "done"
    checkout main
    merge feature
    commit id: "hotfix"
```

## Cheatsheet: common tweaks

- **Direction**: `flowchart LR|TD|BT|RL`
- **Label an edge**: `A -->|label| B`
- **Dashed edge**: `A -.-> B`
- **Thick edge**: `A ==> B`
- **Subgraphs**: `subgraph name ... end`
- **Comments**: `%% this is a comment`
