---
name: architecture-writer
description: Write professional ARCHITECTURE.md documentation following arc42 and C4 model best practices. Structured thinking process: assess system complexity → choose document depth → map components → diagram relationships → document decisions → self-review. Use when the user wants to create architecture documentation, explain system design, says "architecture doc", "ARCHITECTURE.md", "架构文档", "system design", or "how does this system work".
---

# Architecture Writer — System Design Documentation

A disciplined process for writing architecture documentation that helps new contributors understand the system without reading all the code.

## Core Philosophy

Architecture documentation is for **future you and new contributors**. It answers: what are the parts, how do they talk to each other, and why was it built this way? Bad architecture docs describe WHAT (code already shows that). Good ones explain WHY and HOW.

## The Workflow (Must Follow In Order)

### Phase 0: Hard Gate — System Exploration

<HARD-GATE>
Do NOT write ARCHITECTURE.md until you have:
1. Explored the full directory tree and understood module boundaries
2. Identified the main entry points and data flow
3. Found any existing architecture notes, ADRs, or design docs
</HARD-GATE>

Run these checks:
- `ls -R` at top level — what are the top-level directories?
- Find entry points: `main.go`, `index.js`, `__init__.py`, `App.tsx` etc.
- Check for existing architecture docs: `ARCHITECTURE.md`, `docs/architecture/`, `adr/`, `design/`
- Check for configuration files that reveal external dependencies (databases, APIs, queues)
- Read any existing `CLAUDE.md` or `CONTEXT.md` for domain language


### Phase 0.5: Study Real-World Examples (MANDATORY)

Before writing, clone and study the equivalent file from a top-tier open source repo. Extract what real projects actually write — not what templates say they should write. Present findings before drafting.

### Phase 1: Complexity Assessment

Ask **one at a time**:

**Q1: How complex is this system?**
- A) Simple (single app, <5 modules, no external services) → **Light doc (Phase 2a)**
- B) Medium (5-15 modules, 1-2 external services, API surface) → **Standard doc (Phase 2b)**
- C) Complex (microservices, multiple databases, event-driven, 15+ modules) → **Full doc (Phase 2c)**

**Q2: What's the primary audience?**
- A) New contributors who need to understand the system → Focus on modules + data flow
- B) Senior engineers evaluating the design → Focus on decisions + trade-offs
- C) Operations/SRE deploying the system → Focus on deployment + infrastructure
- D) All of the above

### Phase 2: Draft (Based on Complexity)

#### 2a: Light — Simple Systems

```markdown
# Architecture

## Project Structure
\```
src/
├── core/       # Business logic
├── api/        # HTTP handlers
├── db/         # Database layer
└── utils/      # Shared utilities
\```

## Key Modules
| Module | Responsibility | Depends On |
|--------|---------------|------------|
| `core` | Business rules | `db`, `utils` |
| `api` | HTTP endpoints | `core` |
| `db` | Data access | (database) |

## Data Flow
\```mermaid
graph LR
    Client --> API[api]
    API --> Core[core]
    Core --> DB[(database)]
\```

## Key Design Decisions
- [Why we chose this database]
- [Why this framework]
- [Why this project structure]
```

#### 2b: Standard — Medium Systems

Everything in Light, plus:

```markdown
## Architecture Overview
[2-3 paragraphs about the system's high-level design]

## Module Contracts
| Module | Public API | Consumers |
|--------|-----------|-----------|

## Cross-Cutting Concerns
| Concern | Implementation | Notes |
|---------|---------------|-------|
| Logging | [library] | |
| Auth | [approach] | |
| Error handling | [pattern] | |

## Testing Strategy
| Layer | Approach | Tool |
|-------|----------|------|
| Unit | [approach] | [tool] |
| Integration | [approach] | [tool] |
| E2E | [approach] | [tool] |

## ADRs (Architecture Decision Records)
- [ADR-001](docs/adr/001-use-postgres.md): Chose PostgreSQL over MongoDB
- [ADR-002](docs/adr/002-rest-api.md): REST over GraphQL
```

#### 2c: Full — Complex Systems

Everything in Standard, plus:

```markdown
## System Context (C4 Level 1)
\```mermaid
graph TB
    User((User)) --> App[This System]
    App --> DB[(Primary DB)]
    App --> Cache[(Redis)]
    App --> Queue[Message Queue]
    App --> External[External API]
\```

## Container Diagram (C4 Level 2)
\```mermaid
graph TB
    Web[Web App] --> API[API Gateway]
    API --> Auth[Auth Service]
    API --> Core[Core Service]
    Core --> DB[(Database)]
    Core --> Worker[Background Worker]
    Worker --> Queue[(Message Queue)]
\```

## Deployment Architecture
| Environment | Infrastructure | Scaling |
|-------------|---------------|---------|

## Data Architecture
| Store | Purpose | Schema Location |
|-------|---------|----------------|
| PostgreSQL | Primary data | `migrations/` |
| Redis | Session cache | `src/cache/schemas.ts` |

## Security Architecture
[Auth flow, data encryption, network boundaries]

## Failure Modes
| Failure | Impact | Mitigation |
|---------|--------|------------|

## Performance Characteristics
| Operation | Expected Latency | Bottleneck |
|-----------|-----------------|------------|
```

### Phase 3: Self-Review

```
[ ] Every module in the directory tree is accounted for in the doc
[ ] Data flow diagram shows real paths (not aspirational)
[ ] ADRs or key decisions section explains WHY (not just WHAT)
[ ] Module responsibilities are clear and non-overlapping
[ ] Diagrams render correctly (test on target platform)
[ ] No architecture buzzwords without explanation ("event-driven", "microservices")
[ ] Deployment section accurate (not "we'll figure it out later")
[ ] Document matches code — if the doc says "3 services", there are 3 services
```

### Phase 4: User Review

> "ARCHITECTURE.md ready. Please verify: does the module map accurately reflect what's actually in the code? Are the key design decisions correctly captured?"

---

## C4 Model Quick Reference

Use C4 levels for complex systems:

| Level | Name | Scope | Audience |
|-------|------|-------|----------|
| **1** | System Context | System + users + external systems | Everyone |
| **2** | Container | Applications + data stores | Technical team |
| **3** | Component | Modules within a container | Developers |
| **4** | Code | Classes, functions (rarely documented) | Contributors |

Most projects only need Level 1-2 in ARCHITECTURE.md. Level 3-4 live in module-level docs.

## ADR Format

Every significant decision should be documented:

```markdown
## ADR-001: [Decision Title]

**Status:** Accepted | Proposed | Deprecated | Superseded

**Context:** [What was the problem we needed to solve?]

**Decision:** [What did we choose?]

**Consequences:** [What becomes easier? What becomes harder?]

**Alternatives Considered:**
- [Alternative A]: [Why not chosen]
- [Alternative B]: [Why not chosen]
```

## Anti-Patterns

| ❌ Don't | ✅ Do |
|----------|------|
| Diagram-first: draw pretty pictures then write around them | Structure-first: map modules, then diagram |
| Describe what the code does (the code already shows that) | Explain WHY it does it that way |
| "We use microservices" without explaining boundaries | Define what each service owns |
| Architecture doc = copy of directory tree | Modules grouped by responsibility, not by file layout |
| Skip deployment architecture | It's part of the architecture, not a separate concern |
| Make diagrams so complex only you can read them | C4 levels — zoom in progressively |
| Write once and never update | Update when architecture changes (link it to PR checklist) |

## User Interaction Rule

Use AskUserQuestion tool for ALL multiple-choice decisions. Never present A/B/C text options when structured choices exist. One question per decision, lead with a recommendation, include a brief reason.
