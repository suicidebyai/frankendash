# AI Context

> Context and operating guidelines for AI collaborators working on Frankengine.

---

# Project Identity

Frankengine is a local-first AI engineering workspace.

Its purpose is to transform ideas into structured engineering knowledge and implementation plans.

Frankengine is not simply a chatbot interface.

It is a persistent knowledge system designed to help humans and AI collaborate on software development.

---

# Historical Context

Frankengine evolved from an application planning concept.

The original goal was to help transform ideas into:

- Product specifications
- Architecture plans
- Database designs
- Roadmaps
- Implementation strategies

The project evolved into a broader knowledge operating system.

The current architecture is based around:

- Knowledge Objects
- SQLite storage
- Prompt pipelines
- Modular engines
- Local ownership

---

# Core Concepts

## Knowledge Objects

Knowledge Objects are structured pieces of reusable information.

Examples:

- Requirements
- Features
- Decisions
- Architecture
- Tasks
- Research
- Prompts
- Roadmaps

They are the foundation of Frankengine's memory.

---

## Planner Engine

The Planner Engine transforms ideas into structured engineering outputs.

Typical flow:

```
Idea

↓

Discovery

↓

Requirements

↓

Architecture

↓

Database

↓

Implementation Plan

↓

Knowledge Objects
```

---

## SQLite First

SQLite is the canonical source of truth.

Do not introduce alternative storage systems without documenting the architectural reason.

Exports are generated views.

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

## Explain Tradeoffs

When suggesting changes:

Include:

- Why the change helps
- What problem it solves
- Alternatives considered
- Possible downsides

---

## Prefer Incremental Changes

Large rewrites should be avoided unless explicitly approved.

Small, understandable commits are preferred.

---

# Current Development Priorities

The current order of work:

1. Documentation foundation
2. Database design
3. Knowledge Engine
4. Prompt Engine
5. AI Gateway
6. Desktop Application
7. Plugin System

---

# Technology Direction

Planned stack:

- Electron
- React
- TypeScript
- Vite
- SQLite
- Drizzle ORM
- OpenAI-compatible providers
- Local AI models

Technology choices should remain flexible but intentional.

---

# Things Not To Do

AI collaborators should not:

- Create unnecessary abstraction layers
- Add dependencies without reason
- Optimize before understanding requirements
- Replace architecture with generic templates
- Assume SaaS/cloud-first requirements

---

# Working Style

Frankengine values:

- Clear documentation
- Transparent decisions
- Small commits
- Reusable knowledge
- Long-term maintainability

---

# Final Instruction

Understand the system before changing the system.

The goal is not just to make Frankengine work.

The goal is to make Frankengine understandable.