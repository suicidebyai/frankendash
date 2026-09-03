# Programming interface contracts

Status: proposed v0.1 contract. Names below are design notation, not implemented endpoints.
Audience: Engine implementers and Frankendash/Frankenlib adapter authors.
Goal: one behavior contract across chat, CLI, and graphical clients without importing UI or database internals.

## Operations

| Operation | Input | Result | Side effects |
|---|---|---|---|
| submit | Request envelope | Run receipt | Durable run record; no implied external write |
| getRun | Run ID and trusted session | Snapshot and evidence | Read only |
| provideInput | Run ID, question ID, answer, expected revision | Updated receipt | Resume after validation |
| decideApproval | Approval ID, decision, expected plan hash/revision | Accepted or stale/rejected | Grants only exact approved effects |
| cancel | Run ID and expected revision | Cancellation acknowledgement | Stops unsent steps |
| listCapabilities | Trusted session/workspace | Allowed capability descriptions | Read only |
| observe | Run ID and last sequence | Events or cursor-expired response | Read only |

Module-to-module transport follows the in-process host direction. The external client transport (for example IPC or HTTP) remains open. Keep semantics stable across transports.

## Request envelope

Required: contractVersion, requestId, workspaceId, projectId when project-scoped, intent, input, mode, idempotencyKey for every submit that creates a run, and expectedRevision when updating existing state.

The authenticated actor, allowed capabilities, and session validity come from the trusted host. Do not accept client-supplied isAdmin, approved=true, or arbitrary capability lists as authority.

Modes: inspect, plan, execute. Execute still requires action-specific permissions. Intent and operation must be allowlisted. Reject unknown major contract versions and invalid fields before effects.

Example without secrets:
```json
{
  "contractVersion": "0.1",
  "requestId": "example-request-001",
  "workspaceId": "example-workspace",
  "projectId": "example-project",
  "intent": "plan.create",
  "mode": "plan",
  "idempotencyKey": "example-plan-001",
  "input": {
    "goal": "Create a reviewable project brief",
    "constraints": ["No mandatory paid services"]
  }
}
```

These are illustrative IDs, not real workspace records.

## Response envelope

Required: contractVersion, requestId, runId, revision, status, summary, outputs, evidence, warnings, and effects.
Optional: question, approvalRequest, error, nextActions, eventCursor.

status is accepted, running, needs_input, awaiting_approval, verifying, succeeded, partial, blocked, failed, or cancelled. Succeeded requires declared acceptance checks to pass. A plan can succeed without implementing it. outputs carry explicit lifecycle labels.

effects lists each intended/committed/unknown effect separately. evidence contains source ID/URL, revision, check, observedAt, and result. nextActions has at most three user-facing actions.

## Approval request

Include approvalId, runId, action class, target IDs, proposed patch/effects, planHash, expected target revision, cost/privacy consequence, expiry, and whether reversal is possible.

A grant is scoped to that exact action and trusted actor. If target, patch, revision, cost scope, or permissions change, invalidate it. Rejected/expired approval never triggers execution. Never serialize reusable secrets inside an approval.

## Error contract

Return code, safe message, retryable, failedStep, targetRef when safe, committedEffects, and nextAction. Do not forward raw provider traces containing credentials.

| Code | Policy |
|---|---|
| INVALID_INPUT / UNSUPPORTED_VERSION | Fix input; no retry effects |
| CAPABILITY_UNAVAILABLE | Block affected step; report missing capability |
| PERMISSION_DENIED / SESSION_INVALID | Stop affected writes; require authorized session |
| APPROVAL_REQUIRED / APPROVAL_STALE | Obtain exact current approval |
| REVISION_CONFLICT | Fetch current target; reconcile or ask |
| RATE_LIMITED / TRANSIENT_ERROR | Bounded backoff if action is retry-safe |
| OUTCOME_UNKNOWN | Read back effect before any retry |
| VERIFICATION_FAILED | Preserve effect; do not claim completion |
| CANCELLED | Report committed effects and stopped pending work |

## Idempotency and concurrency

Scope an idempotency key to actor/workspace/operation. Same key with the same canonical payload returns the original receipt; same key with different payload returns a conflict. Persist deduplication through Frankenlib before external effects. If durable state is unavailable, do not claim durable replay safety.

A client revision is an optimistic concurrency condition, not an authorization token. Serialize conflicting mutating workflows for MVP. Exact retention and lease implementation belongs to Frankenlib and remains a cross-team decision.

## Compatibility

Within a supported major version, additive optional fields may be ignored. Do not change enum meaning or required-field semantics silently. Record contract and workflow versions on every run.

Acceptance: malformed requests cause zero effects; replay causes no duplicate write; changed payload/key conflict is visible; revoked sessions cannot continue writes; reconnect yields events after the last acknowledged sequence.

## Relationship to the existing blueprint contract

These operations describe the proposed outer run interface. The blueprint-specific operations in ARCHITECTURE_AND_CONTRACTS.md describe work inside a run. Run success does not imply blueprint acceptance or authorization to implement it. Exact naming and transport require reconciliation before coding. No new Defaults module is introduced; core/DEFAULTS.md remains the existing policy document.

## Completed v0.1 proposal: validation and operation payloads
Use contractVersion="0.1" exactly for this draft. Unknown versions return UNSUPPORTED_VERSION. Required envelope and operation payload fields are strictly validated; additive response metadata may be ignored. A later version policy requires an explicit compatibility decision.
Every submit creates a run record and therefore requires idempotencyKey, including plan mode. For the earlier plan.create example, supply idempotencyKey="example-plan-001". inspect/read operations that do not create a run remain read-only.
| Operation | Required payload | Result / concurrency |
| --- | --- | --- |
| submit | intent, mode, input, idempotencyKey | runId/revision/status; repeat returns same receipt |
| getRun | runId | Current authorized snapshot |
| provideInput | runId, questionId, answer, expectedRevision | New run revision or REVISION_CONFLICT |
| decideApproval | runId, approvalId, decision, planHash, expectedRevision | Exact grant/rejection; mismatches APPROVAL_STALE |
| cancel | runId, expectedRevision | Cancellation requested or already terminal; no rollback claim |
| listCapabilities | trusted session only; optional project scope | Allowed operations and availability |
| observe | runId, afterSequence | Ordered events plus cursor or CURSOR_EXPIRED |
Intent allowlist maps to FUNCTIONS. Payload-specific fields include plan.create {goal, constraints[], sourceRefs[]}; decision.record {blueprintId, expectedRevision, contentHash, choice}; artifact.verify {artifactRef, criterionIds[]}. Source references may be empty for a new idea; they must never be fabricated.
A trusted internal authorization context carries actor/workspace/project scope and expiry; it is not accepted from a client JSON flag. Blueprint acceptance and effect authorization are distinct records.

### Effect and evidence objects
Effect: effectId, targetRef, operation, state (planned/attempted/confirmed/unknown/failed/skipped), idempotencyKey, expectedRevision, resultingRevision and evidenceRefs. Evidence: evidenceId, sourceRef, revision, check, result (pass/fail/unknown), observedAt and safe summary. Omit secret values.
A failed or unknown effect never disappears from the response. A terminal run's history is immutable; retries have a linked attempt ID. Add IDEMPOTENCY_CONFLICT, PROVIDER_UNAVAILABLE and CURSOR_EXPIRED to the error codes above. retryable describes whether a bounded retry can be considered, not permission to execute it.
Proposed limits: finite validated request/context/output sizes; explicit timeout/cancellation per adapter. Choose actual numeric limits in the runtime profile; reject excessive payloads before provider calls rather than truncating silently.

