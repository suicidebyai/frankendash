# Frankengine

> Local-first AI operating system for planning, architecture, implementation, and persistent software knowledge.

---

## Vision

Frankengine is an AI-powered engineering workspace designed to transform ideas into complete software projects.

Rather than acting as a chatbot, Frankengine acts as an engineering partner that captures ideas, generates architecture, produces implementation plans, and preserves knowledge in a structured, searchable format.

Frankengine is designed for developers who want complete ownership of their to# FrankDash

> A local-first AI workspace operating system for planning, engineering, knowledge management, and automation.

FrankDash is designed to transform conversations into structured, reusable knowledge while giving users complete ownership of their workspace and data.

Frankengine is the first core module of the platform.

---

# Vision

Modern AI tools generate incredible ideas, but most of that knowledge disappears into chat history.

FrankDash preserves that knowledge by organizing conversations into structured Knowledge Objects that become part of a permanent, searchable workspace.

The goal is not to build another chatbot.

The goal is to build an AI workspace that grows alongside its user.

---

# Core Principles

- Local First
- Developer First
- Provider Agnostic
- SQLite is Canonical
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
FrankDash Workspace
    │
    ├── Frankengine
    ├── Knowledge Library
    ├── Plugin System
    ├── Dashboard
    ├── Projects
    ├── Journal
    └── Automation
            │
            ▼
SQLite
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

# Current Status

FrankDash is currently in active architectural development.

The project is documentation-first to ensure long-term consistency before implementation.

---

# License

MIT (planned)ols and data. Everything runs locally first, with optional AI providers and integrations.

---

## Core Principles

- Local-first
- Developer-first
- AI-assisted, not AI-controlled
- SQLite is the canonical data store
- Knowledge Objects are the primary data model
- Markdown is an export format, not the source of truth
- Every architectural decision is documented
- Every generated artifact is reusable

---

## Philosophy

Software projects accumulate valuable knowledge over time, but traditional chat interfaces lose context as conversations grow.

Frankengine solves this by converting conversations into structured Knowledge Objects that can be searched, related, versioned, and reused.

Ideas become blueprints.

Blueprints become implementation plans.

Implementation plans become software.

Software becomes knowledge.

---

## Architecture Overview

```
Idea
    │
    ▼
Discovery
    │
    ▼
Requirements
    │
    ▼
Architecture
    │
    ▼
Implementation Plan
    │
    ▼
Knowledge Objects
    │
    ▼
SQLite Database
    │
    ▼
Exports
(Markdown • JSON • PDF)
```

---

## Planned Technology Stack

| Layer | Technology |
|--------|------------|
| Desktop | Electron |
| UI | React |
| Language | TypeScript |
| Build | Vite |
| Database | SQLite |
| ORM | Drizzle ORM (proposed) |
| AI Providers | OpenAI, Anthropic, Local LLMs |
| State | Zustand |
| Testing | Vitest + Playwright |

---

## Repository Structure

```
docs/
templates/
packages/
tools/
scripts/
examples/
```

---

## Project Status

Frankengine is currently in active architectural development.

The repository is intentionally being built from first principles.

Documentation is created before implementation so that engineering decisions remain deliberate, reviewable, and maintainable.

---

## License

License to be added.
## Project Status

Frankengine is currently in active architectural development.

The repository is intentionally being built from first principles.

Documentation is created before implementation so that engineering decisions remain deliberate, reviewable, and maintainable.

---

## License

License to be added.