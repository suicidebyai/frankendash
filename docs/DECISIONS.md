# Architecture Decision Records

> A history of important technical and product decisions made during Frankengine development.

---

# Purpose

This document records decisions that affect the direction of Frankengine.

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

Frankengine evolved from earlier planning experiments and prototypes.

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

## SQLite Is the Canonical Source of Truth

### Context

Traditional documentation systems store information as files.

Frankengine requires persistent, searchable, connected knowledge.

### Decision

SQLite will be the primary datastore.

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

- Local ownership
- Simple deployment
- Searchable knowledge
- Structured relationships

Tradeoff:

- Requires thoughtful schema design.

### Status

Accepted

---

# Decision 0003

## Knowledge Objects Are the Core Data Model

### Context

AI conversations contain valuable information, but raw conversations are difficult to reuse.

### Decision

Frankengine stores normalized Knowledge Objects.

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

# Decision 0004

## Prompt Pipelines Generate Structured Data First

### Context

AI output is usually generated as unstructured text.

Frankengine needs predictable, reusable artifacts.

### Decision

Prompt pipelines produce structured JSON before generating documents.

### Alternatives

Generate Markdown directly.

### Consequences

Benefits:

- Multiple output formats
- Validation
- Better storage
- Automation opportunities

Tradeoff:

- More upfront design work.

### Status

Accepted

---

# Decision 0005

## Local First Architecture

### Context

Users should own their projects and data.

### Decision

Frankengine should function locally without requiring cloud infrastructure.

External services are optional integrations.

### Alternatives

Cloud-first SaaS architecture.

### Consequences

Benefits:

- Privacy
- Ownership
- Offline capability
- Lower operating costs

Tradeoff:

- Some collaboration features require additional design.

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

The future should understand not only what Frankengine became, but why.