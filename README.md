# Frankendash

> Local-first AI workspace operating system for planning, engineering, knowledge management, and automation.

---

## Vision

Frankendash is an AI-powered engineering workspace designed to transform ideas into complete software projects. It is built around a clear separation of responsibilities across three canonical system layers: Frankendash (presentation), FrankEngine (reasoning and orchestration), and D.libber (library and persistence).

Frankendash presents and collects information; FrankEngine decides and orchestrates; D.libber stores and organizes.

---

# Core Principles

- Local First
- Developer First
- Provider Agnostic
- D.libber is the canonical library/persistence layer (SQLite is a current implementation)
- Knowledge Objects are the Primary Data Model
- Markdown is a Presentation Layer
- Modular Architecture
- User Owns Their Data

---

# Architecture

```
User
    │
    ▼
Frankendash Workspace
    │
    ├── FrankEngine (brain)
    ├── D.libber (library / persistence)
    ├── Plugin System
    ├── Dashboard
    ├── Projects
    ├── Journal
    └── Automation
            │
            ▼
        Storage (e.g., SQLite)
```

---

# Repository Layout

```
core/
    AI operating principles

docs/
    Product documentation

templates/
    Blueprint templates

packages/
    Application modules

apps/
    Desktop application

scripts/
    Development utilities

```

---

# Documentation

Start here:

- docs/VISION.md
- docs/PRODUCT_SPECIFICATION.md
- docs/ARCHITECTURE.md
- docs/DATABASE.md
- docs/ENGINEERING.md

Core operating documents:

- core/AI_CONSTITUTION.md
- core/DEFAULTS.md
- core/SCOPE_GUARD.md
- core/PARKING_LOT.md
- core/DECISION_HIERARCHY.md

---

# Typical Pipeline (Brainstorming & Planning)

Brainstorming → Ready → project-prep → formal planning → build gate

This pipeline should be treated consistently across documentation: "Ready" indicates the idea has been refined for FrankEngine to begin project preparation. Project-prep includes creating project records, canonical indexes, tasks, and registering resources in D.libber. Only after formal planning and passing the build gate should implementation begin.

---

# Current Status

Frankendash is currently in active architectural development.

The project is documentation-first to ensure long-term consistency before implementation.

---

# License

MIT (planned)
