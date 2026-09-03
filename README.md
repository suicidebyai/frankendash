# FrankEngine V2
Status: working documentation scaffold — not implementation approval.

FrankEngine is the backend host containing AI Reasoning and Frankenlib. Together they turn a user's intent into a bounded, reviewable plan and coordinate authorized execution. It owns the AI system, scope management, defaults resolution, custom instructions, provider-independent prompt workflows, and action decisions. Frankenlib owns durable records, indexes, relationships, provenance, and retrieval. Frankendash owns the UI and is outside this extraction.

## Start here
1. [Defaults](core/DEFAULTS.md): what is assumed, why, and what can be changed.
2. [Constitution](core/AI_CONSTITUTION.md), [custom instructions](core/CUSTOM_INSTRUCTIONS.md), and [scope management](core/SCOPE_GUARD.md).
3. [MVP](docs/PRODUCT_SPECIFICATION.md), [architecture and contracts](docs/ARCHITECTURE_AND_CONTRACTS.md), [acceptance and decisions](docs/ACCEPTANCE_AND_DECISIONS.md).
4. [Source allocation](docs/SOURCES_AND_OWNERSHIP.md) and [project index](docs/PROJECT_INDEX.md).

## Current state
Documentation only. No new repository, moved source files, running engine, enabled scheduler, model integration, or migration is implied. Existing work remains intact. The draft is based on the verified legacy repository snapshot and current ownership instructions; proposed API and runtime details still need approval.

## Smallest useful outcome
Submit an idea; resolve the applicable defaults and instructions; classify scope; produce a structured blueprint; review it; save an accepted version through Frankenlib with provenance. Blueprint approval does not authorize implementation.


## Expanded working scaffold

Use the [V2 project index](docs/PROJECT_INDEX.md) for Drive links to all documents. Added detail includes [programming contracts](docs/INTERFACE_CONTRACTS.md), [functions](docs/FUNCTIONS.md), [run lifecycle](docs/RUN_LIFECYCLE.md), [security](docs/SECURITY_AND_PERMISSIONS.md), [workflows](workflows/WORKFLOW_CATALOG.md), and reusable templates.

Defaults stay in core/DEFAULTS.md, unchanged. Existing constitution, custom instructions, scope guard, and source ownership records are preserved. Frankenlib is a module within the FrankEngine backend; its persistence/search implementation remains separately owned. The earlier hierarchy mismatch is resolved below; runtime and detailed interface approval remain separate gates.

Proposed GitHub landing: a separate feat/frankengine-v2 review branch in suicidebyai/frankendash, with main untouched and no automatic merge. This Drive scaffold does not create that branch or start the build.

## Completed review draft — 2026-09-01
FrankEngine is the backend host containing **AI Reasoning** and **Frankenlib** as sibling modules. AI Reasoning owns interpretation, instructions, scope and workflow decisions. Frankenlib owns persistence, search, indexes, provenance and versioned records. Host services own API/session enforcement, module wiring, shared connectors and credential-provider boundaries. Frankendash consumes the host contract.
The hierarchy warning in the earlier scaffold is resolved against the existing Frankenlib boundary document and the user's current clarification. Runtime/tool versions, host deployment, final contract approval and build authorization remain separate decisions.

Read PRODUCT_SPECIFICATION for the slice, ARCHITECTURE_AND_CONTRACTS for composition, INTERFACE_CONTRACTS for payloads, ADAPTER_CONTRACTS for module ports, and ACCEPTANCE_AND_DECISIONS for checks. Use PROJECT_INDEX for the complete Drive inventory.
First outcome: an offline, explicitly labeled template blueprint can be reviewed, accepted, saved through the Frankenlib contract, retrieved and exported. A memory-only test adapter proves contract behavior, not durability. No provider, real connector, scheduler or third-party plugin is required.
Documentation readiness means every section has an owner, contract, failure outcome and verification path. Software readiness still requires implementation and observed test results. Existing defaults remain in core/DEFAULTS.md.

