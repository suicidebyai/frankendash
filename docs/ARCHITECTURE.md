# Frankengine Architecture

> A local-first AI engineering platform built around structured knowledge, deterministic workflows, and modular components.

---

# Design Philosophy

Frankengine is designed from the inside out.

The engine owns the business logic.

The user interface is simply one way to interact with the engine.

Every major subsystem should remain loosely coupled and independently testable.

---

# High-Level Architecture

```
                User
                  │
                  ▼
        Desktop Application
          (Electron + React)
                  │
                  ▼
          Planner Interface
                  │
                  ▼
          Frankengine Core
                  │
      ┌───────────┼───────────┐
      │           │           │
      ▼           ▼           ▼
 Prompt Engine  AI Gateway  Knowledge Engine
      │           │           │
      └───────────┼───────────┘
                  ▼
            SQLite Database
                  │
      ┌───────────┼───────────┐
      ▼           ▼           ▼
 Markdown      JSON       Future APIs
```

---

# Core Components

## Desktop Shell

Responsible for:

- Window management
- Native menus
- File system access
- Local configuration
- Plugin loading

Technology:

- Electron

---

## User Interface

Responsible for:

- Project management
- Blueprint editing
- Search
- Knowledge visualization
- Settings

Technology:

- React
- TypeScript
- Vite

---

## Frankengine Core

Responsible for:

- Workflow orchestration
- Pipeline execution
- Project state
- Task coordination

The Core contains no UI logic.

---

## Prompt Engine

Responsible for transforming ideas into structured engineering artifacts.

Pipeline stages include:

- Discovery
- Requirements
- Architecture
- Database
- Risks
- Roadmap
- Implementation

Outputs are structured JSON.

---

## AI Gateway

Provides a common interface for AI providers.

Planned providers include:

- OpenAI
- Anthropic
- Local LLMs
- Future integrations

The rest of Frankengine should never depend on a provider-specific SDK.

---

## Knowledge Engine

Responsible for:

- Knowledge Objects
- Relationships
- Search
- Version history
- Metadata
- Future semantic indexing

This is the heart of Frankengine.

---

## Database

SQLite is the canonical datastore.

Nothing else is considered the source of truth.

Markdown, JSON, PDFs, and reports are generated from the database.

---

# Architectural Principles

## Local First

The application should function without cloud services.

Internet connectivity should only be required when communicating with optional AI providers.

---

## Modular

Every subsystem should be replaceable with minimal impact on the rest of the application.

---

## Provider Agnostic

AI providers are interchangeable.

Business logic must never depend on a specific model vendor.

---

## Deterministic

The same inputs should produce predictable workflow outputs whenever possible.

---

## Extensible

Future capabilities should be added through plugins, adapters, or new engine modules rather than modifying existing core systems.

---

# Future Modules

- Multi-agent orchestration
- Semantic search
- Plugin SDK
- Architecture visualization
- Workflow automation
- Git integration
- Knowledge graph visualization
- Local model execution

---

# Guiding Rule

The engine owns the knowledge.

The interface simply presents it.