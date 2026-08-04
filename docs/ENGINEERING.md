# Engineering Guidelines

> Engineering standards and development principles for Frankengine.

---

# Purpose

This document defines how Frankengine should be designed, developed, tested, and maintained.

The goal is not only to build working software.

The goal is to build software that remains understandable as it grows.

---

# Core Engineering Principles

## 1. Documentation Before Implementation

Major features should begin with documentation.

Before writing code, define:

- Problem
- Goals
- Requirements
- Architecture
- Tradeoffs
- Risks

Code should implement decisions, not create them accidentally.

---

## 2. Prefer Simple Foundations

Avoid unnecessary complexity.

Choose solutions that:

- Reduce dependencies
- Minimize maintenance
- Keep ownership local
- Are easy to understand

Complexity must earn its place.

---

## 3. Local First

Frankengine should work without requiring external infrastructure.

External services are integrations, not foundations.

---

## 4. Separation of Concerns

Each layer has a responsibility.

Example:

```
UI

↓

Application Logic

↓

Engine

↓

Database

↓

Storage
```

Avoid placing business logic inside interface components.

---

# Code Organization

## Packages

Planned structure:

```
packages/

desktop/
engine/
database/
ai/
shared/
```

---

## Desktop

Responsible for:

- Application window
- Native integration
- User interface

Should not contain core business rules.

---

## Engine

Responsible for:

- Workflows
- Pipelines
- Business logic
- Orchestration

---

## Database

Responsible for:

- Schema
- Persistence
- Queries
- Migrations

---

## AI

Responsible for:

- Provider connections
- Model communication
- Prompt execution

---

## Shared

Responsible for:

- Types
- Utilities
- Common contracts

---

# Dependency Philosophy

Dependencies should be evaluated carefully.

Before adding a dependency consider:

- Is it necessary?
- Can we build it ourselves?
- Does it create long-term maintenance?
- Does it lock us into a vendor?

Fewer dependencies create more ownership.

---

# Testing Strategy

Testing should exist at multiple levels.

## Unit Tests

For:

- Functions
- Utilities
- Data transformations

---

## Integration Tests

For:

- Database operations
- Engine workflows
- AI pipelines

---

## End-to-End Tests

For:

- Complete user workflows
- Desktop application behavior

---

# Git Standards

Commits should:

- Have one purpose
- Explain the change
- Avoid mixing unrelated work

Preferred format:

```
type: description

Examples:

docs: add database architecture

feat: create knowledge object storage

fix: correct pipeline validation
```

---

# Architectural Decisions

Important decisions must be recorded.

Use:

```
docs/DECISIONS.md
```

A decision should include:

- Context
- Decision
- Alternatives
- Consequences
- Date

---

# AI Development Rules

AI assistants contributing to Frankengine should:

- Read documentation first
- Preserve existing architecture
- Avoid unnecessary rewrites
- Explain tradeoffs
- Ask before making major changes

AI should accelerate engineering, not replace engineering judgment.

---

# Quality Standard

Before merging changes:

- Documentation updated
- Tests considered
- Architecture respected
- No unnecessary complexity introduced

---

# Guiding Principle

Good engineering is not about writing the most code.

It is about creating systems that remain understandable after the original creator is gone.