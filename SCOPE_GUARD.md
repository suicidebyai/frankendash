# AI Scope Management
Status: draft implementation specification for established scope rules.
Owner: FrankEngine. Frankenlib persists decisions and history.

## Input
Current objective, active priorities, accepted decisions, MVP requirements, permissions, dependencies, proposed action, and relevant source evidence.

## Classification
- Required: explicitly requested and permitted, necessary to meet the accepted objective, or a genuine blocker-removal step.
- Recommended: useful to the same objective without material scope expansion; explain before promoting if tradeoffs matter.
- Parked: speculative improvement or future feature not needed for the current deliverable.
- Blocked: missing permission, dependency, security approval, or consequential decision.
- Rejected: incompatible with a standing constraint, with a reason and a safe alternative if available.

Required does not mean automatically authorized. A request to plan a migration does not authorize moving data.

## Focus and drift
Keep at most three active priorities. Prefer completion over novelty. Distinguish accidental drift from an explicit decision to switch goals. Preserve parked ideas with a reason, dependencies, and a promotion condition. No automatic promotion because a model finds an idea attractive.

## Planning gate
Before implementation, establish MVP outcome and non-goals, project boundaries, effective defaults/instructions, contracts, dependencies, acceptance tests, unresolved risks, and explicit build authorization. A draft may be reviewed and revised while this gate remains closed.

## Proposed output
scope_decision: classification, action_id, objective_id, rationale_summary, source_refs, permission_state, blockers, next_action, policy_version.
Return concise evidence-based rationale, not hidden reasoning. Persist the decision through Frankenlib.

## Parking lot for this MVP
Third-party plugin runtime; SSH/shell execution; workspace code editor; multi-agent autonomy; visual workflow builder; automatic repo extraction; paid-provider fallback; vector retrieval before lexical retrieval works. UI features remain outside this project, not reassigned to the library.

## Deterministic decision procedure
1. Resolve the objective and existing tracked task IDs; reconcile their current source state.
2. Classify the proposed work using the five categories above.
3. Independently evaluate permission, prerequisite and evidence gates. A Required classification does not bypass a Blocked permission outcome.
4. Return one primary classification, reasons tied to source IDs, missing gates and the next permitted action.
5. Persist authorized focus/parking changes through Frankenlib with expected revision.
An explicit "complete the FrankEngine V2 docs" request is an intentional focus change. A subsequent question about flib ownership is relevant clarification and does not increment drift. Earlier unfinished UI tasks remain open; they are not silently completed or deleted.
Scope examples: adding a required response schema is Required; adding a theme editor to Engine docs is Parked/outside Engine; an unspecified paid provider is Blocked pending a policy choice; a request to treat a title match as task identity is Rejected on integrity grounds.
Completion: the selected deliverable passes its declared acceptance checks and required record reconciliation. Drift counters reset on meaningful progress or an explicit priority replacement; parked and suspended tasks do not nag.

