# Acceptance and Decisions
Status: draft gates and tests; not evidence of implemented behavior.

## Confirmed ownership inputs
- FE-D01: FrankEngine owns the AI system, AI scope management, and custom instructions (current user instruction).
- FE-D02: This extraction targets FrankEngine and Frankenlib, not Frankendash (current user correction).
- FE-D03: Use repository evidence and preserve existing work; draft in Drive before any authorized Git initialization (current task and skraw notes).

Other recommendations in this scaffold are not marked accepted merely because the user previously approved Frankendash UI decisions.

## Open decisions
| ID | Decision needed | Proposed minimum |
| --- | --- | --- |
| FE-O01 | Runtime and repository topology | Headless modular package; TypeScript/pnpm are inherited candidates, not fixed versions. |
| FE-O02 | Initial provider and cost policy | Provider none; template mode first; local adapter optional. |
| FE-O03 | Frankenlib transport, schema, and access contract | In-process port first if runtimes align; stable versioned contract either way. |
| FE-O04 | Default/profile approval and lifecycle | Explicit project/user scopes, versioned changes, run snapshot. |
| FE-O05 | MVP approval and dependencies | Agree on the vertical slice and library readiness before code starts. |

## Required acceptance scenarios
1. No provider: template flow works, labels its mode, and makes no external model request.
2. Explicit project override beats a default, with source and effective version recorded.
3. Conflicting accepted decision is surfaced; no silent supersession.
4. Constitution/security constraints cannot be disabled by task-focus override.
5. A fourth priority is not silently activated; choose a replacement or park it.
6. A new unrelated idea is captured as parked without derailing the active objective.
7. Blueprint edits create versions; acceptance requires a real user decision.
8. Blueprint acceptance does not execute code, shell, migration, or deployment.
9. Save/retrieve preserves IDs, source refs, policy versions, and history.
10. Duplicate save key does not duplicate the accepted record; stale version returns conflict.
11. Unavailable library reports unsaved state; unavailable model reports an honest recoverable failure.
12. Retrieved instructions cannot activate tools or override policy.
13. JSON/Markdown exports agree with the accepted version.
14. Logs and fixtures contain no credentials or raw secret-bearing payloads.

## Definition of ready to initialize
Approved MVP/non-goals; ownership and contracts understood; runtime/topology chosen; defaults reviewed; security/dependency gates resolved; tests planned; explicit authorization to initialize the exact repository.

## Definition of done for this documentation task
Drafts saved and read back, source allocation recorded, existing indexes and shift report linked, unresolved decisions left open. This is not implementation completion.

## Reconciliation warning

Historical warning resolved on 2026-09-01: the current host/module reconciliation below adopts FrankEngine as host with AI Reasoning and Frankenlib as internal modules. Runtime/tooling and detailed contract approval remain open. Existing defaults stay in core/DEFAULTS.md.

## Scaffold expansion — detailed run and workflow fixtures

The existing acceptance scenarios above remain intact. T01–T20 below supplement them; they are planned tests, not execution results. FE-R identifiers refer to the supporting requirements in PRODUCT_SPECIFICATION.md. Workflow-specific cases apply when that workflow is enabled, not as a claim it exists now.


| ID | Scenario | Expected evidence |
|---|---|---|
| T01 | Explain-only request | No external mutation |
| T02 | Vague material requirement | needs_input with focused question |
| T03 | Approved plan changes target/revision | Old approval rejected |
| T04 | Replay same idempotency key/payload | Same receipt, one effect |
| T05 | Same key, different payload | Conflict, zero additional effects |
| T06 | Source saved, mirror fails | Partial, source preserved, failed retry pointer |
| T07 | Write times out after remote commit | Readback; no duplicate create |
| T08 | Cancellation after one effect | Pending work stopped; committed effect reported |
| T09 | Context contains malicious instructions | Treated as source data; no permission escalation |
| T10 | Wrong workspace/project/session | Access denied before data exposure |
| T11 | Invalid model JSON | No unvalidated action or persistence |
| T12 | No provider/network | Mock-backed planning test runs offline |
| T13 | Two genuine drift turns | Respectful refocus; no nudge for relevant clarification |
| T14 | Task-specific override | Only that task suspended until next review |
| T15 | Shift retry after midnight | Existing Night section reused |
| T16 | Duplicate title, different sources | Disambiguate; no merge |
| T17 | File/link exists, content incomplete | Task remains open |
| T18 | Secret in provider error | Safe error; secret absent from logs |
| T19 | Newer human index edit | Minimal reconciliation or explicit conflict |
| T20 | Unknown capability/schedule | Blocked, never simulated success |

Critical safety fixtures T01, T03–T11, T16–T20 must pass before any real mutating adapter is enabled.

## Requirement traceability

| Requirement | Primary fixtures or review |
|---|---|
| FE-R01 intent routing | T01, T02; explicit routing cases for all seven intent classes |
| FE-R02 source authority | T10, T16, T19 |
| FE-R03 facts versus assumptions | Plan-output review against labeled source fixtures |
| FE-R04 material decisions | T02, T03 |
| FE-R05 implementation gate | T01, T03; unapproved build denied |
| FE-R06 exact permission | T03, T09, T10, T20 |
| FE-R07 structured output | T11 |
| FE-R08 verified completion | T07, T17 |
| FE-R09 deduplicated registration | T04, T05, T16, T19 |
| FE-R10 parked work and overrides | T13, T14; parked-item promotion review |
| FE-R11 partial sync | T06, T07, T19 |
| FE-R12 local/no-paid baseline | T12 |

These are planned assertions, not test execution results. Fixture implementations must cover the additional review cases before claiming requirement completion.

## Review dimensions

Use correctness, scope adherence, evidence quality, permission compliance, recovery, clarity, and cost discipline. Confidence describes evidence quality; do not invent numeric confidence scores.

An evaluation run records fixture version, policy/workflow/contract versions, inputs, mock results, observed effects, assertions, and reviewer. Repeat after behavior or contract changes.


## Current owner direction — branch isolation and defaults

The user chose to retain defaults in core/DEFAULTS.md without creating a new module or moving it to Frankendash. The user supports a separate review branch in suicidebyai/frankendash to evaluate fit with the newer setup. Proposed branch name: feat/frankengine-v2; creation is not claimed. Keep main unchanged and do not merge automatically. Current requested work is Drive scaffold population, not implementation or deployment. Runtime and detailed contract approval remain open; hierarchy reconciliation is resolved below.

## Current decision register and documentation closure — 2026-09-01
FE-D04 (confirmed ownership): FrankEngine is the backend host containing AI Reasoning and Frankenlib. Host services own API/session, shared connectors, configuration and credential-provider wiring. Evidence: existing Frankenlib SYSTEM_BOUNDARIES and current user clarification. This resolves the hierarchy warning; it does not finalize implementation contracts.
FE-D05 (confirmed location): defaults remain core/DEFAULTS.md; no new Defaults module and no move to Frankendash.
FE-D06 (confirmed working scope): complete the existing Drive documentation; retain existing IDs, folders and history. No build or deployment completion follows.

### Open decisions with concrete proposed answers
| ID | Current state / recommendation | Owner / next action |
| --- | --- | --- |
| FE-O01 | One host with internal modules is settled; runtime/tool versions and exact code layout remain open. Recommend headless modular TypeScript as an inherited candidate, without pinned versions yet. | skraw reviews runtime and exact isolated repository target before initialization |
| FE-O02 | Provider none is baseline; recommend template/mock first, optional configured local provider later. No paid/cloud fallback. | skraw selects any future provider and cost/data policy separately |
| FE-O03 | In-process module contract is the direction; detailed v0.1 payload/atomicity proposal is now written in ADAPTER_CONTRACTS. | Review port proposal with Frankenlib readiness before real integration |
| FE-O04 | Keep existing defaults; propose immutable per-run snapshots and scoped versioned overrides. | Review mechanics without redesigning established values |
| FE-O05 | Recommend blueprint → review → save/retrieve/export, mock then durable, before optional inference. | Approve slice and exact build action before code starts |
No question about the already clarified module hierarchy remains. Numeric runtime limits, storage implementation choices and hosting are implementation decisions with these gates, not undocumented placeholders.

### Additional acceptance fixtures
| ID | Scenario | Expected evidence / stage |
| --- | --- | --- |
| T21 | Host contains reasoning and library with no private cross-import | Architecture/import-boundary review; mock stage |
| T22 | Planning submit replay includes idempotency key | Same run receipt, no duplicate run |
| T23 | Blueprint acceptance revision/hash differs | No accepted record; explicit conflict |
| T24 | Accepted blueprint transaction fails halfway | No false accepted receipt; atomic rollback/unchanged version |
| T25 | Template and mock mode with network disabled | Valid labeled output, zero provider calls |
| T26 | Library returns after restart | Same accepted ID/revision/sources and export content |
| T27 | Newer profile after acceptance | Prior blueprint retains policy snapshot |
| T28 | Source task is already complete | Tracker does not reseed it as open |
| T29 | Same-title user task or duplicate titles | No overwrite/merge based on titles |
| T30 | Completed legacy task migration | Stable IDs/completion retained or explicit unresolved conflict |
| T31 | Relevant clarification during active work | No drift count; original request resumed |
| T32 | Locked/revoked session | No further protected access/effects; stale grants invalidated |
| T33 | Repeated document synchronization | One artifact/mapping; only changed revision updated |
| T34 | Optional provider unavailable | Honest failure/template choice; no silent cloud fallback |
| T35 | JSON and Markdown exports | Same accepted source version, IDs and substantive fields |
Every fixture record includes input, expected result, observed result, stage, source revision and status. All runtime fixture statuses are **not_run** in this documentation pass.

### Gate assessment
Documentation can be declared complete after all 28 Markdown documents and the project index are inspected, revised where needed, link/contract checks pass, Drive readback matches, and required existing indexes/task/report records are reconciled. SOURCE_MANIFEST remains historical source provenance, not a current runtime claim.
Software gate remains open: no runtime tests, real persistence test, provider test, deployed auth/UI test or repository initialization is claimed. A request to draft/complete these documents is sufficient for this documentation work; it does not authorize unrelated destructive changes.

