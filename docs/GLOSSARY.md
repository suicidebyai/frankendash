# Frankengine Glossary

> Canonical terminology used throughout Frankengine.

---

# Purpose

This glossary defines the official language of Frankengine.

Every document, feature, database schema, and codebase component should use these terms consistently.

When introducing a new concept, add it here.

---

# AI Gateway

The subsystem responsible for communicating with AI providers.

Responsibilities include:

- Provider abstraction
- Model selection
- Request execution
- Response normalization
- Error handling

The AI Gateway should isolate Frankengine from vendor-specific SDKs.

---

# Artifact

A generated representation of structured knowledge.

Examples:

- Markdown
- JSON
- PDF
- HTML
- Source Code

Artifacts are generated outputs.

Artifacts are **not** the source of truth.

---

# Blueprint

A structured engineering plan generated from an idea.

Typical sections include:

- Overview
- Requirements
- Architecture
- Database
- Risks
- Roadmap
- Tasks

Blueprints are composed of multiple Knowledge Objects.

---

# Conversation

A sequence of interactions between the user and one or more AI providers.

Conversations create Knowledge Objects but are not themselves the permanent knowledge model.

---

# Decision

A documented architectural or product choice.

Decisions should explain:

- Context
- Rationale
- Alternatives
- Consequences

Decisions are stored in `docs/DECISIONS.md`.

---

# Engine

The collection of services responsible for Frankengine's business logic.

The engine contains no user interface code.

---

# Export

A rendered representation of structured data.

Exports include:

- Markdown
- JSON
- PDF
- HTML

Exports are disposable.

Knowledge remains permanent.

---

# Knowledge Object

The fundamental unit of information inside Frankengine.

Examples include:

- Requirement
- Feature
- Task
- Architecture
- Decision
- Prompt
- Roadmap Item
- Research Note
- Bug
- API Specification

Knowledge Objects are versioned, searchable, and reusable.

---

# Planner Engine

The subsystem responsible for transforming ideas into structured engineering knowledge.

Typical stages include:

- Discovery
- Requirements
- Architecture
- Database
- Risks
- Roadmap
- Implementation

---

# Pipeline

A deterministic workflow executed by the Planner Engine.

Pipelines transform structured inputs into structured outputs.

Each pipeline is versioned.

---

# Project

A logical workspace containing conversations, Knowledge Objects, artifacts, and implementation history.

---

# Prompt

An instruction provided to an AI model.

Prompts are inputs.

Knowledge Objects are outputs.

---

# Relationship

A typed connection between Knowledge Objects.

Examples:

- depends_on
- implements
- references
- supersedes
- relates_to
- generated_from

Relationships allow Frankengine to build a connected knowledge graph.

---

# SQLite

The canonical datastore for Frankengine.

Everything ultimately persists here.

Other formats are generated from SQLite.

---

# Workspace

The complete environment in which one or more projects exist.

Future versions of Frankengine may support multiple workspaces.

---

# Future Terms

Additional concepts expected in later versions:

- Agent
- Plugin
- Workflow
- Semantic Index
- Memory Graph
- Event Bus
- Automation
- Extension
- Workspace Module

---

# Guiding Principle

Shared language creates shared understanding.

When everyone uses the same words to describe the same concepts, architecture becomes easier to build, discuss, and maintain.