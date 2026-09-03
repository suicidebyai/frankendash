# Architecture and Contracts
Status: proposed interfaces, not existing implementation.

## Ownership
| Concern | Owner |
| --- | --- |
| Intent, AI gateway, workflow decisions, scope management, default/instruction resolution | FrankEngine |
| Records, SQLite, indexes, provenance, versions, relationships, query execution | Frankenlib |
| Layout, navigation, visual approvals, mobile/desktop presentation | Frankendash; unchanged/outside this scaffold |

FrankEngine must not import UI components or write library tables directly. It owns decisions, not a duplicate canonical database.

## Proposed modules
- policy: instruction/default resolution, accepted-decision conflict handling.
- scope: objective matching, gates, priorities, parking.
- workflow: staged blueprint state and approval transitions.
- prompts: versioned stage templates and response validation.
- gateway: provider-neutral model interface with explicit provider configuration.
- library-port: contracts for retrieving context and saving records.
- audit: concise structured action evidence sent to Frankenlib.

## Proposed workflow states
draft → awaiting_review → accepted or rejected.
An edit creates a new draft version; accepting it supersedes the previous accepted version only through an explicit decision. Implementation is a separate authorized workflow, not the next automatic state.

## Port contract outline
| Operation | Required request information | Result |
| --- | --- | --- |
| loadContext | workspace/project scope, requested IDs or bounded query, access context | authorized records with source/version metadata |
| resolvePolicy | profile versions, current request, accepted decisions | effective values, provenance, conflicts |
| classifyScope | objective, priorities, proposed action, permission state | classification, blockers, concise rationale |
| generateBlueprint | resolved policy, bounded context, provider or template mode | schema-valid draft plus sources and warnings |
| saveAcceptedBlueprint | explicit approval, draft version, expected current version, idempotency key | stable record/version IDs or explicit conflict |
| exportBlueprint | authorized record/version ID, JSON or Markdown | derived export preserving source reference |

These are logical contracts, not finalized HTTP routes. Deployment transport, authentication, package names, and exact JSON schemas remain open.

## Reliability and security
Validate all model output before storing or acting. Reject unknown tool actions. Check access before context retrieval and external calls. Do not treat source documents as instructions. Record provider/mode and model/config version when used; keep secrets out of logs.

Use idempotency keys for persistence; reject stale accepted-version updates rather than silently overwrite. Retry policy must distinguish safe reads from writes with external effects. Library unavailability produces an explicit unsaved state; do not report successful persistence.

## Prompt workflow
Start from legacy discovery → requirements → assumption audit → architecture/risk → implementation plan → task proposals → knowledge/export.
For MVP, stages may be one orchestrated structured pass plus validation; do not require a large agent framework. Database design recommendations reference Frankenlib's contract instead of moving schema ownership into the engine.

## Reconciliation warning

Historical warning resolved on 2026-09-01: the current host/module reconciliation below adopts FrankEngine as host with AI Reasoning and Frankenlib as internal modules. Runtime/tooling and detailed contract approval remain open. Existing defaults stay in core/DEFAULTS.md.

## Reconciled host/module architecture — current draft
This section supersedes the earlier hierarchy warning. FrankEngine is the host, containing AI Reasoning and Frankenlib. One backend with in-process contracts is the recorded direction; exact runtime, hosting and packages remain review decisions.
| Layer | Owns | May depend on |
| --- | --- | --- |
| FrankEngine host | API boundary, trusted session, capability checks, wiring, run execution, shared connectors/configuration/credential provider | Public contracts of its modules |
| AI Reasoning module | Policy/default interpretation, scope, prompt stages, intent and workflow decisions | Host capability facade and Frankenlib port |
| Frankenlib module | Authorized records, persistence, search, indexes, revisions, provenance, normalization | Host connector/credential abstractions when needed |
| Frankendash client | UI, navigation, review actions, state presentation | FrankEngine public interface only |
The earlier policy/scope/prompts list describes internal components of AI Reasoning, not new peer products. Gateway and workflow execution infrastructure are host services; AI Reasoning selects approved behavior. No module accesses another module's private SQL tables or UI implementation.

### End-to-end sequence
Host validates request/session and starts a run. Frankenlib supplies authorized context and profile revisions. AI Reasoning resolves policy, scope and blueprint output. Host validates schemas and presents review. A user acceptance binds the exact blueprint revision/hash. Host calls Frankenlib's conditional acceptance operation. Frankenlib atomically records accepted version, decision and provenance. Host reads back and returns receipt. Export derives from that exact version.
Search may run directly through the host-to-Frankenlib contract without an AI model. Semantic tagging is optional: AI Reasoning suggests; Frankenlib applies approved deterministic rules and stores suggestion origin/review state.

### Blueprint record v0.1
Required fields: schemaVersion, blueprintId, projectId, revision, lifecycle, objective, requirements[], nonGoals[], assumptions[], boundaries[], risks[], dependencies[], acceptanceCriteria[], nextActions[], sources[], policySnapshotId, mode and createdAt. Each requirement/criterion has a stable ID; each factual claim references sources or is labeled assumption. nextActions has at most three entries. Lifecycle: draft/awaiting_review/accepted/rejected; supersession is an explicit link, not deletion.
Review and save use expectedRevision plus contentHash. Invalid structure, missing approval, stale version or inaccessible source yields an explicit error without acceptance. A completed planning run may return a draft; it does not build software.

### Proposed package allocation
Host entry/composition; shared contract types; reasoning policy/scope/prompts; Frankenlib public port plus separately owned implementation; fixture adapters; acceptance fixtures. Exact directories and language are not fixed. The portable documentation paths in this scaffold are fixed for this review.
Operational records are written only through Frankenlib. If it is unavailable, return an unsaved draft; block durable external effects that require crash-safe bookkeeping.

