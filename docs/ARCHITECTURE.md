# Architecture

> High-level architecture and system boundaries for Frankendash and its core modules.

---

# Design Philosophy

The system is designed with a clear separation of concerns:

- Frankendash (presentation): UI, workspace surfaces, navigation, dashboards, and workflow visibility.
- FrankEngine (brain): reasoning, orchestration, workflow rules, project-prep triggers, automation, decisions about what happens next.
- D.libber (library/persistence): structured records, relationships, metadata, workflow status and history.

Every major subsystem should remain loosely coupled and independently testable.

---

# High-Level Architecture

```
                User
                  │
                  ▼
          Frankendash (UI / Workspace)
                  │
                  ▼
             FrankEngine (Core / Brain)
                  │
                  ▼
               D.libber (Library / Persistence)
                  │
                  ▼
   Storage implementation (e.g., SQLite, other)
```

Interaction model (canonical):

Frankendash → FrankEngine → D.libber → FrankEngine → Frankendash

---

# Core Components

## Frankendash (Presentation)

Responsible for:

- UI
- Workspace surfaces
- Navigation
- Dashboards
- User interactions
- Workflow visibility
- Project and task presentation
- Status and progress surfaces

Frankendash should present and collect information, but it should not own core reasoning, orchestration logic, or persistent system state.

---

## FrankEngine (Core / Brain)

Responsible for:

- Reasoning
- Workflow orchestration
- Pipeline execution
- Workflow rules
- Project-preparation triggers
- Automation
- Decision logic
- Scope and readiness evaluation
- Coordination between the interface, library layer, and connected tools

FrankEngine decides what should happen next and coordinates execution.

---

## D.libber (Library / Persistence)

Responsible for:

- Persistent state
- Structured records
- Relationships
- Project and workspace metadata
- Workflow status and history
- Canonical references and identifiers
- Stored outputs required by FrankEngine and Frankendash
- Searchable workspace knowledge
- Organized project and document references
- Library-style retrieval and organization

D.libber stores and organizes system knowledge and state. The underlying storage implementation (e.g., SQLite) may change without changing D.libber's role.

---

# Architectural Principles

## Local First

The application should function without cloud services. Internet connectivity should only be required when communicating with optional AI providers.

---

## Modular

Every subsystem should be replaceable with minimal impact on the rest of the application.

---

## Provider Agnostic

AI providers are interchangeable. Business logic must never depend on a specific model vendor.

---

## Deterministic

The same inputs should produce predictable workflow outputs whenever possible.

---

# Guiding Rule

Frankendash presents. FrankEngine decides and orchestrates. D.libber stores and organizes.
