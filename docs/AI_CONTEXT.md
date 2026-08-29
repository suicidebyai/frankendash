# AI Context

> Context and operating guidelines for AI collaborators working on Frankendash and FrankEngine.

---

# Project Identity

Frankendash is a local-first AI engineering workspace. FrankEngine is the reasoning and orchestration module within the platform.

Its purpose is to transform ideas into structured engineering knowledge and implementation plans.

Frankendash is not simply a chatbot interface; it is a persistent knowledge system designed to help humans and AI collaborate on software development.

---

# Core Concepts

## Knowledge Objects

Knowledge Objects are structured pieces of reusable information. They are stored and organized by D.libber and orchestrated by FrankEngine, and presented by Frankendash.

Examples:

- Requirements
- Features
- Decisions
- Architecture
- Tasks
- Research
- Prompts
- Roadmaps

---

## FrankEngine

FrankEngine is the planner and orchestration module that transforms ideas into structured engineering outputs and coordinates with D.libber and Frankendash.

Typical flow:

Brainstorming → Ready → project-prep → formal planning → build gate

---

## D.libber

D.libber is the library/persistence layer. It stores canonical references, project metadata, workflow status/history, and searchable workspace knowledge. The underlying database (e.g., SQLite) is a current implementation.

---

# AI Collaboration Rules

AI contributors should:

## Read Before Changing

Before modifying architecture:

- Read documentation
- Understand existing decisions
- Check DECISIONS.md
- Identify constraints

---

## Preserve Architecture

Do not:

- Replace systems without justification
- Introduce unnecessary frameworks
- Remove previous decisions without review

---

## Prefer Incremental Changes

Small, understandable commits are preferred.
