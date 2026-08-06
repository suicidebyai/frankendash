# System Defaults

Version: 1.0

## Purpose

System Defaults define Frankengine's assumed configuration when a project does not explicitly specify a preference.

Defaults are conveniences, not permanent rules.

They may be overridden by:

1. Explicit user instructions
2. Accepted project decisions
3. Project requirements
4. Architecture constraints

Defaults should minimize unnecessary questions while remaining flexible.

---

# Platform

Workspace

FrankDash

Planning Module

Frankengine

Primary Platform

Desktop

Architecture

Local First

Offline Support

Preferred

---

# Technology

Language

TypeScript

Frontend

React

Desktop Runtime

Electron

Build Tool

Vite

Package Manager

pnpm

Node Version

Latest LTS

---

# Database

Canonical Database

SQLite

ORM

Drizzle ORM (Preferred)

Search

SQLite Full-Text Search (FTS)

Embeddings

Disabled by default

---

# Knowledge

Canonical Storage

Knowledge Objects

Conversation Storage

Normalized into Knowledge Objects

Markdown

Presentation / Export only

JSON

Primary interchange format

Version History

Enabled

---

# AI

Architecture

Provider Agnostic

Default Provider

None

Local LLM Support

Preferred when practical

Cloud AI

Optional

Prompt Pipeline

Frankengine Prompt Engine

Structured Output

Preferred

---

# Project Structure

Repository

Monorepo

Modules

Plugin-capable

Documentation

Markdown

Configuration

JSON

Assets

Organized by module

---

# Plugins

Plugin System

Enabled

Plugin Isolation

Preferred

Core Modules

Always available

Third-party Plugins

Optional

---

# Authentication

Default

None

PIN Protection

Optional

User Accounts

Only when required

Cloud Authentication

Disabled by default

---

# Networking

Internet Access

Only when required

Cloud Sync

Disabled by default

Telemetry

Disabled

Analytics

Disabled

---

# Development

Testing

Vitest

End-to-End

Playwright

Linting

ESLint

Formatting

Prettier

CI/CD

Optional

---

# Scope

Default Strategy

Smallest viable implementation

Optimization

Only after functionality

Architecture Changes

Require justification

Speculative Features

Move to Parking Lot

Future Ideas

Move to Parking Lot

---

# Documentation

Every document should be understandable on its own.

Important context may be repeated when it improves clarity.

Only one document should contain the complete authoritative definition of a shared rule.

---

# Decision Resolution

When multiple instructions conflict, Frankengine follows:

1. User Request
2. AI Constitution
3. Accepted Decisions
4. Project Specification
5. Scope Guard
6. System Defaults
7. Parking Lot

---

# Override Policy

Defaults are assumptions.

They must never override:

- User intent
- Accepted architectural decisions
- Explicit project requirements

When a default conflicts with a higher-priority instruction, the higher-priority instruction always wins.

## Guiding Principle

Defaults exist to reduce repetitive questions, not to reduce flexibility.

Frankengine should make reasonable assumptions when appropriate, while remaining transparent about those assumptions.

When uncertainty affects architecture, security, data integrity, or user intent, Frankengine should ask rather than guess.

The objective is efficient collaboration, not silent automation.