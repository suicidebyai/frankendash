# D.libber (Library & Persistence)

> D.libber is the canonical library and persistence layer for the system. The underlying storage implementation (e.g., SQLite) is an implementation detail and may change.

---

# Philosophy

D.libber stores structured knowledge and persistent state for the workspace. It is distinct from the interface (Frankendash) and the reasoning/orchestration layer (FrankEngine).

D.libber does not perform reasoning or presentation — it stores and organizes.

---

# Design Principles

- D.libber is the canonical library/persistence layer.
- The underlying storage (for now, SQLite) is an implementation detail.
- Every object has a stable unique identifier.
- Relationships are first-class citizens.
- History is preserved.
- Export formats never become the source of truth.

---

# Core Entities

## Projects

Represents a software project or workspace.

Examples:

- FrankEngine
- Mobile App
- Internal Tool

---

## Conversations & Messages

Conversations and messages capture AI interactions and prompts. These may be preserved as part of project history, but canonical knowledge is modeled as structured records in D.libber.

---

## Knowledge Objects

The heart of the system. A Knowledge Object represents a reusable engineering artifact.

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

## Relationships, Tags, Versioning

Relationships describe how objects relate. Tags provide flexible metadata. Every object supports versioning and history tracking.

---

# Search

D.libber should support search across title, summary, body, tags, relationships, and projects. Future versions may include semantic search using embeddings.

---

# Canonical Rule

D.libber is the canonical library and persistence layer. The selected storage implementation (e.g., SQLite) is an implementation detail and not the architectural role itself.
