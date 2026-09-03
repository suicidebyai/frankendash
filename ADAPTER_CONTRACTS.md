# Adapter contracts

Status: proposed integration seam; no SDK dependency selected.

## Frankenlib port

Operations required by Engine behavior: resolve/read authorized references, retrieve scoped context, save a versioned decision/artifact proposal, append safe run events, read/write a checkpoint conditionally, deduplicate operation keys, and persist external-reference mappings.

Return stable IDs, revisions, canonical locations, authorization-filtered records, and explicit outcomes. Query implementation, indexes, schemas, migrations, taxonomy storage, retention, and backups stay in Frankenlib.

If the port is unavailable, explain degraded read/draft mode. Do not perform durable external actions while claiming crash-safe orchestration without durable bookkeeping.

## External-system port

Describe system ID, supported operations, permission/effect class, schemas, version preconditions, idempotency support, rate limits, readback operation, and error mapping.

A connector may offer read only even when its account has wider permission. Report actual capability availability each session. Never scrape or repurpose credentials to work around blocked access.

Mutation receipt: system, targetId, operationId if provided, status, resultingRevision, canonicalUrl, and readbackEvidence. Unknown outcome remains unknown until reconciled.

## Scheduler/event-source port

A schedule description includes stable ID, timezone, cadence, enabled state, prompt/workflow version, last result, and configured destination scope. Updating instructions must preserve schedule identity/cadence/enabled state unless explicitly changed.

External document events require event ID, source ID/revision, event time, authenticated origin, deduplication, and replay policy. A conversational trigger is not a deployed watcher.

## Frankendash client seam

Expose run snapshots, input/approval requests, capability availability, effect/evidence summaries, and allowed commands. UI implementations choose layout and visual styling, not permission outcomes.

Acceptance: a fixture adapter can be swapped for a real adapter without moving workflow rules into the UI or database package.

## Frankenlib contract v0.1 — complete review surface
Frankenlib is an internal FrankEngine module, not a required standalone service. Host composition injects this port; storage internals stay inside Frankenlib.
Every request uses trusted workspace/project scope, contractVersion and requestId. Writes additionally require idempotencyKey and expectedRevision where updating an existing record.
| Method | Input | Successful result |
| --- | --- | --- |
| context.read | sourceRefs or bounded query, allowed profile IDs | Authorized items with source/revision and truncation warning |
| blueprint.get | blueprintId, optional revision | Blueprint plus actual lifecycle/revision |
| blueprint.saveDraft | Valid blueprint, expectedRevision if existing | Stable ID, draft revision and contentHash |
| blueprint.accept | blueprintId, revision, contentHash, trusted acceptanceRef | Accepted revision and linked decision receipt |
| events.append | runId, expectedSequence, safe events | Assigned monotonic sequences |
| checkpoint.put/get | runId and conditional snapshot | Persisted checkpoint/version or missing |
| operation.reserve/complete/get | Scoped key, canonical payload hash, effect receipt | Reserved/existing/conflict/unknown state |
| externalRef.upsert | project, source system, source ID, artifact type, revision | Existing or new mapping; no title-only identity |
Atomic boundary: blueprint.accept writes the accepted version, explicit supersession, decision and provenance together. Partial transaction failure returns no accepted success. Engine must not emulate atomicity with several uncoordinated writes.
Typed failures: unauthorized, not_found, invalid, revision_conflict, unavailable, idempotency_conflict and outcome_unknown. Not_found does not reveal whether another workspace owns the ID.
Contract fixtures: same-key replay, changed-payload conflict, stale acceptance, scope isolation, unavailable storage, restart with unknown effect, source-title collision and lossless export. In-memory fixtures label durability=false.

## Shared host adapter rules
Connectors and credential providers are host services usable by both modules. Library-specific ingestion/normalization stays in Frankenlib. Reasoning-specific prompt choice stays in AI Reasoning.
A connector descriptor includes actual read/write/readback capability and native conditional-update/idempotency support. Missing native guarantees must be reported; do not promise exactly-once remote effects. Unknown outcomes block retries until reconciled. Credentials are resolved at invocation; only non-secret references enter records.

