# Vision

> Build the ultimate local-first AI engineering operating system.

---

## Platform and Modules

Frankendash provides the workspace and presentation surfaces. FrankEngine is the core reasoning and orchestration module. D.libber is the library and persistence layer.

Frankendash exists to help developers transform ideas into production-ready software while preserving every important architectural decision, implementation detail, and lesson learned.

---

## The Problem

Modern AI tools generate incredible ideas, but they suffer from several limitations:

- Conversations become difficult to navigate.
- Architectural decisions are forgotten.
- Documentation becomes fragmented.
- Project knowledge is scattered across chats and markdown files.
- Valuable implementation details are lost over time.

Software projects deserve persistent memory.

---

## The Solution

Frankendash introduces a structured knowledge approach built around reusable Knowledge Objects and a clear architectural separation:

- Frankendash (presentation)
- FrankEngine (reasoning & orchestration)
- D.libber (library & persistence)

Every interaction becomes structured data; documentation becomes one representation of that knowledge.

---

## Core Goals

### Local First

Users own their data. The application should function entirely offline except when communicating with optional AI providers.

---

### AI Provider Agnostic

FrankEngine should support multiple AI providers through a common abstraction layer. Changing providers should never require changing the application architecture.

---

### Knowledge Over Documents

Frankendash treats documents as views. D.libber is the canonical library/persistence layer (the underlying storage, such as SQLite, is an implementation detail).

---

### Engineering Before Code

Architecture precedes implementation. Every major feature should begin with:

- Discovery
- Requirements
- Architecture
- Risks
- Implementation Plan

Only then should code be written.

---

## Typical Pipeline

Brainstorming → Ready → project-prep → formal planning → build gate

Ready indicates an idea has been refined enough for FrankEngine to begin project preparation.

---

## Guiding Principle

Ideas are temporary. Knowledge is permanent. Frankendash exists to preserve the latter.
