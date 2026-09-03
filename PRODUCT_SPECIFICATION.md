# Product Specification
Status: V2 MVP proposal, pending review.

## Goal
Make a user's idea understandable, bounded, and finishable before generating implementation work. Apply the user's actual defaults and instructions, keep scope visible, and preserve approved outcomes as structured knowledge.

## MVP vertical slice
1. Accept an idea and selected project context through a headless application boundary.
2. Load authorized defaults, instructions, decisions, and knowledge through Frankenlib.
3. Resolve instructions and classify scope; surface consequential conflicts.
4. Produce a structured blueprint: objective, requirements, non-goals, assumptions, architecture boundaries, risks, dependencies, acceptance criteria, and no more than three next actions.
5. Let the user accept, edit, or reject it. No automatic implementation.
6. Save an accepted version, its sources, decision history, and effective policy versions through Frankenlib.
7. Retrieve it by stable ID; produce JSON and readable Markdown exports without changing the source of record.

## Non-goals
UI routes/themes, desktop/mobile shell, editor/SSH, full automation platform, third-party plugins, multi-user SaaS, autonomous code migration, embedding-first search, and a second persistence implementation inside FrankEngine.

## Proposed staged delivery
A. Approve contracts/defaults and resolve the runtime decision.
B. Implement deterministic scope/default resolution and template-mode blueprint flow with a library test adapter.
C. Integrate the approved Frankenlib persistence boundary; verify a full save/retrieve round trip.
D. Add one explicitly configured local-provider adapter if desired. Cloud providers remain optional and separately gated.

No configured model must be a valid honest operating state. Template output cannot be marketed as live AI generation. Workflow transitions and validation can be deterministic; generated prose is not guaranteed deterministic.


## Scaffold expansion — supporting functional requirements

The existing blueprint-first MVP above remains the working scope. The following requirements describe the broader Engine behavior contract; index/shift coordination is staged after the mock blueprint loop, not silently added to the first build.


| ID | Requirement | Completion evidence |
|---|---|---|
| FE-R01 | Classify explain, diagnose, plan, change, capture, verify, and coordinate requests | Routing fixtures |
| FE-R02 | Resolve project and source authority before writes | Target/authority log |
| FE-R03 | Separate facts, assumptions, proposals, and unknowns | Structured plan fields |
| FE-R04 | Ask about material scope, cost, security, and ownership choices | Input/approval fixture |
| FE-R05 | Gate application implementation behind an approved plan | Denied-write test |
| FE-R06 | Bind actions to exact targets and permission | Authorization record |
| FE-R07 | Validate structured pipeline output before use | Schema rejection tests |
| FE-R08 | Verify contents and acceptance criteria before completion | Evidence references |
| FE-R09 | Reconcile artifact indexes without duplicates | Replay test |
| FE-R10 | Preserve parked work and user overrides | Focus-state fixtures |
| FE-R11 | Report per-destination partial sync | Failure fixture |
| FE-R12 | Work without mandatory cloud or paid inference | Offline mock run |


Detailed run contracts: [INTERFACE_CONTRACTS](INTERFACE_CONTRACTS.md). Function catalog: [FUNCTIONS](FUNCTIONS.md). Later operational flows: [workflow catalog](../workflows/WORKFLOW_CATALOG.md).

## MVP completion journey and cut line
Target user: skraw operating a personal workspace from an available client. FrankEngine supplies backend behavior, not a new UI. The confirmed host contains AI Reasoning and Frankenlib; the initial host transport can be tested without a browser.
Scenario: submit a project idea with no model configured → resolve permitted project/default context → generate an explicitly labeled template blueprint → identify missing material inputs → user reviews the exact revision → save accepted version through Frankenlib → retrieve by ID → export matching JSON/Markdown.
The mock slice may use fixture context and an in-memory Frankenlib adapter; its receipt must say test/non-durable. A usable persisted slice requires the real Frankenlib port and restart verification. Provider integration is optional after the persisted slice, not a prerequisite.

### Scope by delivery stage
| Stage | Included | Exit evidence |
| --- | --- | --- |
| Documentation | Complete review specification and explicit decisions | Inventory, link/schema consistency, Drive readback |
| Mock behavior | Validation, policy, scope, blueprint/review flow, fixture ports | Offline assertions and zero unintended external effects |
| Durable behavior | Frankenlib round trip, events, conditional acceptance and replay | Restart, conflict and readback tests |
| Optional inference | One approved local provider through gateway | Labeling, output validation, cancellation/failure tests |
| Later coordination | One authorized connector/workflow at a time | Per-target readback and retry evidence |
Proposed quality requirements: bounded context and outputs; explicit cancellation; no secret-bearing logs; unauthorized projects excluded before retrieval; stable IDs/revisions across exports; honest unknown/partial states. Performance targets must be measured on the chosen runtime and device before setting service-level claims.
Documentation completion does not approve runtime choices, initialize a repository, migrate records, deploy a backend or enable automated writes. These remain distinct gates in ACCEPTANCE_AND_DECISIONS.

