# Database Architecture

> SQLite is the canonical source of truth for Frankengine.

---

# Philosophy

Frankengine does not store documents.

Frankengine stores knowledge.

Markdown, JSON, PDF, and other formats are generated views of structured data.

Every meaningful piece of information becomes a Knowledge Object.

---

# Design Principles

- SQLite is the only canonical datastore.
- Every object has a stable unique identifier.
- Relationships are first-class citizens.
- History is preserved.
- Nothing is overwritten without versioning.
- Export formats never become the source of truth.

---

# Core Entities

## Projects

Represents a software project or workspace.

Examples:

- Frankengine
- Mobile App
- Internal Tool

---

## Conversations

Stores AI interactions associated with a project.

A conversation contains messages but also produces reusable knowledge.

---

## Messages

Individual prompts and responses.

Messages are immutable.

---

## Knowledge Objects

The heart of Frankengine.

A Knowledge Object represents a reusable engineering artifact.

Examples:

- Product Specification
- Feature
- Architecture Decision
- Database Table
- API Endpoint
- User Story
- Prompt Pipeline
- Roadmap Item
- Task
- Bug
- Risk
- Research Note

Knowledge Objects exist independently of conversations.

---

## Relationships

Knowledge is connected.

Relationships describe how objects relate.

Examples:

```
Feature
    implements
Architecture

Architecture
    depends_on
Database

Task
    belongs_to
Sprint

Decision
    supersedes
Decision
```

Relationships are directional and versioned.

---

## Tags

Flexible metadata for categorization.

Examples:

- backend
- frontend
- ai
- ui
- sqlite
- security
- roadmap

---

## Decisions

Stores architectural decisions.

Each decision records:

- title
- rationale
- alternatives
- consequences
- date
- status

Nothing important should live only inside commit messages.

---

## Artifacts

Generated outputs.

Examples:

- Markdown
- JSON
- PDF
- HTML
- Code Generation

Artifacts are disposable.

Knowledge Objects remain permanent.

---

# Versioning

Knowledge evolves.

Every object supports:

- version
- created_at
- updated_at
- superseded_by
- previous_version

No destructive edits.

---

# Search

Search should operate across:

- title
- summary
- body
- tags
- relationships
- projects

Future versions will include semantic search using embeddings.

---

# Future Tables

- Prompt Pipelines
- Workflow Runs
- AI Providers
- Plugins
- Agents
- Embeddings
- Graph Cache

---

# Canonical Rule

SQLite owns the truth.

Everything else is generated from it.