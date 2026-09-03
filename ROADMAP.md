# Engine roadmap

Status: proposed implementation sequence; no dates or runtime completion implied.

## Phase 0 — reviewable documentation

Complete source reconciliation, boundaries, policies, interfaces, workflow specs, test fixtures, and open decisions.
Exit: user reviews the new contract/MVP proposals; unresolved choices are explicit.

## Phase 1 — deterministic mock vertical slice

Implement request validation, scope/permission checks, run transitions, fixture capability invocation, verification, and response envelopes.
Exit: critical acceptance fixtures pass without paid inference or external writes.

## Phase 2 — prompt pipeline and gateway

Add one configured provider adapter, structured-output validation, versioned prompt stages, privacy/cost controls, and failure normalization.
Exit: malformed outputs never execute; model provider can be replaced without changing policy.

## Phase 3 — Frankenlib contract integration

Use durable run/event, decision, artifact, and external-reference ports supplied by Frankenlib.
Exit: restart/readback/idempotency fixtures pass. Database implementation remains inside FrankEngine's Frankenlib module, outside host orchestration and AI Reasoning.

## Phase 4 — bounded operational workflows

Enable manual capture/registration and shift reconciliation with one approved real connector at a time.
Exit: correct project mapping, minimal updates, verified readback, no duplicate artifacts, and honest partial failures.

## Phase 5 — approved automation

Update or enable a verified existing schedule/event source with explicit scope.
Exit: cadence/timezone/state readback plus an observed test run; no duplicate schedules.

Deferred: autonomous builders, untrusted plugins, general shell access, and broad always-on watchers.

Immediate review priorities: contract shape, first runnable slice, and unresolved authority/target decisions. Approval of documents alone does not activate any phase.

## Reconciled delivery order — supersedes phase ordering above
The earlier Phase 2 provider-before-storage order was provisional. The current recommendation is:
1. Review complete documentation and select runtime/target plus contract/default approvals.
2. Build the offline template/mock blueprint flow with an explicitly non-durable fixture adapter.
3. Integrate the internal Frankenlib module for durable acceptance, retrieval, export, restart and idempotency.
4. Optionally add one approved local model through the gateway. Provider none remains valid.
5. Add a bounded manual capture/index/shift workflow with one real connector and required readback.
6. Only then consider independently approved scheduler/event-source activation.
The host/module hierarchy is resolved; runtime/tool versions, final package layout, hosting and implementation authorization remain open. Library schema/search choices belong to Frankenlib's existing review, not a duplicate Engine database plan.
Each phase requires the preceding acceptance evidence relevant to its effects. Passing a mock fixture never clears the durability gate; a document update never clears the deployed UI gate.
No dates are fabricated. Owner reviews open decisions; implementation records actual dependencies and test outcomes. Deferred features remain in SCOPE_GUARD with explicit revisit conditions rather than becoming hidden MVP requirements.

