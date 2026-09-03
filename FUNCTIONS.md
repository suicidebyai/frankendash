# Engine function catalog

Status: proposed callable surface. All operations use [interface contracts](INTERFACE_CONTRACTS.md).

| Function | Trigger/input | Output | Effect/permission |
|---|---|---|---|
| intent.resolve | User request and scoped context | Intent, scope, missing questions | Read/process |
| plan.create | Goal, constraints, evidence | Structured brief and plan | Draft only until capture authorized |
| scope.evaluate | Proposed addition and current objective | Required/Recommended/Parked/Blocked/Rejected plus rationale | No mutation |
| readiness.evaluate | Requirements and acceptance | Missing gates / ready status | Never grants build permission |
| decision.record | Explicit choice and source | Versioned decision receipt | Authorized durable write |
| capability.invoke | Allowlisted operation and validated arguments | Normalized result | Exact operation permission |
| artifact.verify | Deliverable and acceptance checks | Evidence and remaining gaps | Read unless check needs explicit effects |
| artifact.register | Verified artifact identity/revision | Registry/index results | Authorized per-target updates |
| capture.request | Selected content and capture cue | Reusable content and capture receipt | Existing research protocol applies |
| sync.reconcile | Scoped sources/destinations | Changed fields and per-target results | No blanket all-app authority |
| shift.review | Prior shift and available sources | Top 3, follow-ups, blockers | Read/draft |
| shift.update | Verified events/decisions/docs | Existing log/mirror updates | Authorized existing targets |
| focus.track | User-selected tasks | Tracked task references | Durable focus metadata |
| focus.override | Specific task and explicit override | Suspension through next review | Not permission escalation |
| settings.resolve | Request/project/workspace preferences | Effective values plus origin | Read/process |

Each implementation declares input schema, output schema, required capabilities, effect class, idempotency policy, cancellation policy, validation, and acceptance tests. A function catalog entry is not proof a capability exists.

Do not expose unrestricted executeCode or arbitrary shell as an MVP function. Provider output cannot select new privileged capabilities or change its own permission policy.

## Ownership and validation matrix
Intent resolution, scope evaluation, readiness and settings resolution are AI Reasoning operations. The host dispatches authorized workflow/effect operations. Frankenlib implements durable record/search/index operations behind its public port.
| Function group | Required identity/input | Validation / failure |
| --- | --- | --- |
| plan.create | project, goal, constraints, source refs, mode | Missing consequential input → needs_input; invalid schema → failed |
| decision.record | exact draft/revision/hash, explicit choice | Stale/missing approval → blocked; persist atomically |
| capability.invoke | registered capability ID, validated args, trusted grant | Unknown/unavailable/unauthorized → zero invocation |
| artifact.verify/register | source ID/revision, acceptance criteria, destinations | Incomplete content → not complete; destination failure → partial |
| capture.request | selected material, source, requested taxonomy action | Unclear source/taxonomy → question or unclassified proposal |
| sync.reconcile | bounded source/target mappings and revisions | Ambiguous identity → conflict; unknown effect → readback |
| focus.track/override | stable task references and relevant user instruction | Title collision → no merge; override affects one task |
Use scope classifications exactly as SCOPE_GUARD: Required, Recommended, Parked, Blocked, Rejected. A catalog shorthand is not a different enum.
Every mutating function requires a persisted operation key before a remote effect. get/list/evaluate functions do not secretly mutate domain records; separately declared audit writes remain visible.
Function outputs have lifecycle and evidence labels. "ready" means readiness criteria pass, not build authorization. "verified" describes a specific check. "synced" requires all requested destination readbacks.
Acceptance IDs and stage allocation live in ACCEPTANCE_AND_DECISIONS; do not create independent contradictory completion rules here.

