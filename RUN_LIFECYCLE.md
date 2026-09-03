# Run lifecycle and events

Status: proposed v0.1.

## Transitions

- accepted → running after validation and context resolution.
- running → needs_input when a material question remains.
- running → awaiting_approval before an unapproved side effect.
- needs_input/awaiting_approval → running only after a matching valid reply.
- running → verifying after attempted effects.
- verifying → succeeded when acceptance evidence is complete.
- running/verifying → partial if some intended effects succeeded but required work remains.
- running/verifying → blocked for external prerequisites, or failed for unrecoverable processing.
- blocked → running only after the missing prerequisite is resolved and session, permissions, target revision, and pending effects are revalidated.
- accepted → failed for invalid input, or blocked when required capabilities are unavailable; neither transition authorizes effects.
- any nonterminal state → cancelled when cancellation is honored.

Terminal states: succeeded, partial, failed, cancelled. Blocked may resume after revalidation. Partial/failed retries create a linked follow-up attempt; do not rewrite historical events to manufacture success.

Input and approval waits have configured expiries. Expiry moves the run to blocked with a reason; it never implies consent. A rejected approval blocks the affected plan until the user revises it or cancels the run.

## Event envelope

Fields: eventId, runId, sequence, timestamp, contractVersion, workflowVersion, type, safe payload, correlationId. Sequence is monotonic within a run, not across all workspaces.

Types include run.accepted, step.started, input.required, approval.required, approval.decided, effect.attempted, effect.confirmed, verification.completed, destination.sync_result, run.partial, run.failed, run.cancelled, and run.succeeded.

Persist safe event metadata through Frankenlib. Clients deduplicate by eventId/sequence. Reconnect with last-seen sequence; expired cursors require a current snapshot, not guessed replay. Timestamps are informational; sequence determines run order.

## Cancellation/restart

Check cancellation before provider invocation and before each side effect. If a remote request is already sent, mark pending outcome and read it back. Never say cancellation reversed a completed mutation.

On restart restore checkpoint, query unknown effects, validate session and target revisions, then resume authorized pending work. No automatic replay of a stale approval.

No hidden reasoning stream is required. Progress shows steps, decisions, evidence, and effects only.

Blueprint lifecycle is separate: draft, awaiting_review, accepted, or rejected as recorded in ARCHITECTURE_AND_CONTRACTS.md. A run can succeed by producing an unapproved blueprint. The proposed run states do not replace blueprint review states.

## State invariants and recovery table
Only the host advances run state after validated module results. AI Reasoning may recommend a transition; Frankenlib persists conditional state/events.
| Condition | State/outcome | Next permitted action |
| --- | --- | --- |
| Missing material answer | needs_input | Accept matching question/revision response |
| Missing exact effect authorization | awaiting_approval | Validate grant or remain blocked |
| Library unavailable before durable effect | blocked | Produce unsaved draft if within scope |
| Remote write outcome unknown | verifying, then partial/blocked as appropriate | Readback; never blind replay |
| All requested acceptance checks pass | succeeded | Return evidence and lifecycle labels |
| User cancels after a committed effect | cancelled with committed effects listed | Stop pending work; explicit compensating action only |
Concurrent updates require expected run revision. The host rejects stale responses and duplicate terminal transitions. A repeated cancel of a terminal run returns the current terminal receipt.
Do not mark effect.confirmed from an HTTP success alone when required readback is missing. destination.sync_result is independent of artifact lifecycle. A saved draft plus failed required mirror yields partial.
On process restart, load checkpoint and operation reservations, reconcile unknown outcomes, then revalidate session/permissions and source revisions. A restart cannot resurrect expired approval.
Acceptance: event sequence increases; replay deduplicates; cancellation records committed effects; accepted blueprint and succeeded planning run remain independent; retry attempts preserve earlier terminal history.

