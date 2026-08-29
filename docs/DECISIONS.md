# Architecture Decision Records

> A history of important technical and product decisions made during FrankEngine development.

---

# Purpose

This document records decisions that affect the direction of FrankEngine.

The goal is to preserve:

- Why decisions were made
- Alternatives considered
- Tradeoffs accepted
- Future context

A decision should not disappear simply because the conversation where it happened is gone.

---

# Decision Format

Each decision follows this structure:

```
Decision Number

Title

Context

Decision

Alternatives

Consequences

Status

Date
```

---

# Decision 0001

## Start With a Clean Repository

### Context

FrankEngine evolved from earlier planning experiments and prototypes.

The previous project history contained valuable ideas, but also duplicated documentation and changing architectural assumptions.

### Decision

Create a new repository with a clean foundation while preserving previous work as reference material.

### Alternatives

Continue modifying the previous repository.

### Consequences

Benefits:

- Cleaner history
- Clearer architecture
- Easier onboarding
- Intentional commits

Tradeoff:

- Some migration effort is required.

### Status

Accepted

---

# Decision 0002

## D.libber Is the Canonical Library / Persistence Layer (SQLite as current implementation)

### Context

Traditional documentation systems store information as files. The platform requires persistent, searchable, connected knowledge.

### Decision

D.libber will be the architectural library/persistence layer. The underlying storage implementation (for now, SQLite) is an implementation detail and may change.

Generated formats such as:

- Markdown
- JSON
- PDF
- HTML

are exports and views, not canonical storage.

### Alternatives

- Markdown-first storage
- Cloud database-first architecture
- Multiple synchronized storage systems

### Consequences

Benefits:

- Clear separation between architecture and storage implementation
- Searchable knowledge
- Structured relationships
- Persistent state

Tradeoff:

- Requires thoughtful schema and library design.

### Status

Accepted

---

# Decision 0003

## Knowledge Objects Are the Core Data Model

### Context

AI conversations contain valuable information, but raw conversations are difficult to reuse.

### Decision

FrankEngine stores normalized Knowledge Objects in D.libber.

Examples:

- Requirements
- Architecture decisions
- Features
- Tasks
- Research
- Prompts
- Roadmaps

### Alternatives

Store complete conversations only.

### Consequences

Benefits:

- Reusable knowledge
- Better search
- Relationships between concepts
- Long-term project memory

Tradeoff:

- Requires extraction and normalization.

### Status

Accepted

---

# Future Decisions

Future records should cover:

- Technology stack
- Database schema
- Plugin system
- AI provider architecture
- Agent workflows
- Security model
- Deployment strategy

---

# Guiding Principle

Every important decision should leave a trail.

The future should understand not only what the platform became, but why.
