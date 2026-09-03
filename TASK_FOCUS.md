# Task focus

Status: user-requested behavior; runtime implementation pending.

At shift/status/top-three reviews offer tracking for selected tasks. Link to existing task identities. Record goal, acceptance criteria, current state, source/evidence, and next action.

Count meaningful user turns without progress, not raw messages. Relevant clarification, debugging, evidence collection, or intentional priority changes are not drift.

After two qualifying turns, briefly identify the unfinished tracked request and ask whether to resume, park, or replace it. After repeated drift be firmer and direct without shaming. Parked tasks do not trigger nudges.

“sudo override skill -force,” or an equivalent explicit instruction, suspends refocus for the specific relevant task until the next shift/status review. It does not complete, delete, park, or grant new permissions. If several tasks could match, ask which one.

At the next review reconsider that task for tracking; do not erase the suspension history. Mark completion only when acceptance evidence is inspected and required record updates are done. Store focus state through Frankenlib; display it through Frankendash.

## Focus record and transition rules
Proposed record: taskRef {system, projectId, taskId}, goal, acceptanceRefs[], state (tracked/parked/suspended/completed), sourceRevision, lastProgressAt, qualifyingDriftTurns, suspensionReason/expiryReviewId and nextAction.
Asana remains operational authority in this workspace. Reconcile its current status before choosing priorities; prototype defaults do not override completed records. Store focus metadata separately from the task's authoritative completion field.
| Event | Result |
| --- | --- |
| Relevant clarification or implementation progress | Reset drift; keep task tracked |
| Explicit new objective | Intentional switch; retain unfinished work for review |
| Two qualifying drift turns | One respectful resume/park/replace prompt |
| Explicit park | Parked; no nudges |
| Task-specific force override | Suspended until next shift/status review |
| Completion claim without evidence | Remains unfinished; identify missing criterion |
| Verified completion and required sync | Completed focus state; source update/readback |
Do not match by titles alone. Known seed migration requires stable IDs, provenance/version and uniqueness. Preserve edited/user-created tasks and their completion state; an ambiguous seed set is left intact with a review warning.
Regression cases: clean start must reflect authoritative completed status; same-title user task is preserved; duplicate titles do not imply seed identity; completed IDs/status survive migration; mixed/edited tasks survive; rerun creates zero duplicates. The earlier prototype report recorded four failures, but these are future Engine acceptance cases, not claimed fixed here.
A user question such as "is flib a module now?" during this documentation task is relevant clarification. Resume completing the documents rather than prompting a refocus.

