# Workflow catalog

Status: v2 workflow specification, not live automation state.

| Workflow | Trigger | Owner / result | Gate |
|---|---|---|---|
| Idea to blueprint | Explicit planning request | Engine / structured reviewable plan | Material questions resolved |
| Authorized action | Approved scoped plan | Engine / effect plus readback | Exact permission |
| Capture and register | Capture cue or authorized artifact completion | Engine invokes Frankenlib/adapters | Identity + protocol |
| Index reconcile | Explicit sync or approved event | Existing records updated | Source authority + revision |
| Shift change | User request or verified schedule | Existing log and mirrors | Prior shift + source identity |
| Task focus | User-selected tracked tasks | Focus state and refocus cues | No implicit tracking of everything |
| Completion review | Claimed finished deliverable | Acceptance evidence | All required checks |
| Error recovery | Known failure/unknown effect | Safe resume or blocker | Readback before replay |

## Idea-to-blueprint procedure

Resolve active project and intended user. Capture goal and constraints. Produce requirements and acceptance checks. Audit assumptions. Generate only relevant design/risk sections. Break approved work into tasks with dependencies and evidence. Ask for design/build approval separately. Capture the result only in authorized destinations.

## Completion gate

The deliverable exists; contents were inspected; acceptance checks passed; required user approvals exist; dependent records are updated when required by the task; material blockers are resolved; evidence is recorded.

When document authoring is complete but index sync fails, report “draft complete, registration partial.” Do not mark a combined author-and-sync task finished.

See [document lifecycle](DOCUMENT_LIFECYCLE.md), [shift change](SHIFT_CHANGE.md), and [task focus](TASK_FOCUS.md).

## Stage ownership and availability
All listed workflows are specifications. The first build contains idea-to-blueprint plus review/export with fixture ports. Capture, external index sync, shift writes and schedules require later adapters/effect gates.
Host services execute and enforce workflows. AI Reasoning supplies intent, scope and decisions. Frankenlib stores state, evidence and mappings and performs query/index operations. A workflow cannot grant itself a connector or approval.
Each workflow is versioned and registered with input/output schema, effects, required capabilities, idempotency key scope, cancellation, recovery, and acceptance IDs.
Example plan run: validate request → read fixture context → resolve policy → produce template blueprint → validate → return draft. Later acceptance run: validate exact version/hash → persist through Frankenlib → read back → export if requested. No automatic code execution follows.
Operational workflow failure: preserve successful effects, report each failed/unknown destination, and link a retry attempt. A successful capture does not imply the shift mirror or external registry succeeded.
Retirement preserves workflow versions referenced by historical runs. New versions apply to new runs; resuming old runs requires explicit compatibility validation.

