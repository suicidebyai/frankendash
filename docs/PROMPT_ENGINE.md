# Prompt Engine

> The Prompt Engine transforms ideas into structured engineering knowledge.

---

# Philosophy

Large Language Models generate text.

Frankengine generates structured engineering artifacts.

The Prompt Engine is responsible for orchestrating deterministic workflows that convert raw ideas into reusable Knowledge Objects.

The engine should always produce structured JSON first.

Markdown, HTML, PDF, and other formats are generated from that structured data.

---

# Design Principles

- Pipeline driven
- Modular
- Deterministic
- Provider agnostic
- Versioned
- Reusable

Every stage has one responsibility.

---

# High-Level Pipeline

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
Assumptions
    │
    ▼
Architecture
    │
    ▼
Database Design
    │
    ▼
Risk Analysis
    │
    ▼
Implementation Plan
    │
    ▼
Task Breakdown
    │
    ▼
Knowledge Objects
    │
    ▼
SQLite
    │
    ▼
Exports
```

---

# Pipeline Stages

## 1. Discovery

Purpose:

Understand the problem.

Outputs:

- Problem Statement
- Goals
- Constraints
- Unknowns

---

## 2. Requirements

Purpose:

Convert ideas into engineering requirements.

Outputs:

- Functional Requirements
- Non-functional Requirements
- Acceptance Criteria

---

## 3. Assumption Audit

Purpose:

Separate facts from assumptions.

Outputs:

- Verified Facts
- Assumptions
- Risks
- Open Questions

---

## 4. Architecture

Purpose:

Recommend system architecture.

Outputs:

- Components
- Services
- Data Flow
- Technology Choices

---

## 5. Database Design

Purpose:

Design persistent storage.

Outputs:

- Entities
- Relationships
- Constraints
- Versioning Strategy

---

## 6. Risk Analysis

Purpose:

Identify technical and project risks.

Outputs:

- Risks
- Mitigations
- Tradeoffs

---

## 7. Implementation Planning

Purpose:

Generate actionable work.

Outputs:

- Milestones
- Tasks
- Dependencies
- Estimates

---

## 8. Knowledge Extraction

Purpose:

Normalize outputs into Knowledge Objects.

Every pipeline stage contributes reusable engineering knowledge.

---

# JSON First

The Prompt Engine never generates Markdown directly.

Instead it produces structured JSON.

Example:

```json
{
  "project": {},
  "requirements": [],
  "architecture": {},
  "knowledgeObjects": [],
  "tasks": []
}
```

Renderers transform this JSON into:

- Markdown
- HTML
- PDF
- Documentation
- Reports
- Future formats

---

# AI Provider Abstraction

Prompt pipelines never call an AI provider directly.

Instead they communicate through the AI Gateway.

This allows switching providers without changing the pipeline implementation.

---

# Versioning

Prompt pipelines are versioned.

Projects record which pipeline version was used to generate their artifacts.

This allows:

- Reproducibility
- Comparison
- Improvement tracking
- Migration strategies

---

# Pipeline Configuration

A pipeline should define:

- Name
- Version
- Purpose
- Required Inputs
- Processing Steps
- Expected Outputs
- Validation Rules

Example:

```json
{
  "pipeline": "software_blueprint",
  "version": "1.0",
  "inputs": [
    "idea",
    "constraints"
  ],
  "outputs": [
    "architecture",
    "requirements",
    "roadmap",
    "knowledge_objects"
  ]
}