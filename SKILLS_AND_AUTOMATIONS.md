# Skills, functions, workflows, and automations

Status: specification. This document installs nothing.

- Function: bounded callable operation with a schema.
- Skill: reusable instructions selecting safe operations and verification.
- Workflow: versioned sequence with state, gates, and results.
- Automation: an actually configured scheduler/event source invoking a workflow.

A skill is not a daemon. Writing “every time a document is created” does not subscribe to an external event feed.

## Skill contract

Declare name, purpose/triggers, required context, supported capabilities, permissions, steps, failure behavior, and completion evidence. Load only relevant instructions. Versions must be inspectable and updates require review. Skills cannot grant themselves extra permissions.

Existing Run Cross-Project Shift behavior must be inspected before modification. Installed skills and scheduled runs must be verified separately; this scaffold neither installs nor enables them.

## Automation update procedure

1. List/read existing matching automations.
2. Match purpose, source, destinations, timezone, and stable ID.
3. Preserve cadence and enabled/disabled state unless changed by user instruction.
4. Update the bounded workflow instructions, not unrelated automation settings.
5. Read back ID, prompt/version, timezone, cadence, and enabled state.
6. Record what changed and the next expected run, without claiming the run succeeded.

If listing or update is unavailable, provide a draft and blocker; do not create a possible duplicate. New event watchers require explicit source/trigger, credentials/permissions, deployment, replay handling, and a verification event.

## Shift automation prompt template

“Use the current cross-project shift workflow. Verify existing report/index identities. Read the prior shift, current project sources, and operational tasks. Present at most three priorities and ask which to track. Reconcile verified decisions, artifacts, task states, and follow-ups into existing destinations only. Update the active shift section and required mirrors; report per-system failures honestly. Never infer completion from a filename or create replacement shift logs.”

The template does not override approved canonical ownership, personal source maps, or host permissions.

## Manifest, activation and lifecycle
A proposed skill manifest contains skillId, version, triggers[], ownerModule, requiredCapabilities[], allowedEffectClasses[], workflowVersion, verificationCriteria[], sourceRefs and reviewStatus. Installation and invocation are separate records.
AI Reasoning chooses relevant approved instructions. The host checks available capabilities and scope. Frankenlib stores manifest versions and execution provenance. A downloaded skill cannot expand capability policy.
Activation states: draft, reviewed, installed, enabled, suspended, retired. These describe separate facts: a reviewed file may be uninstalled; an installed skill may have no enabled schedule.
A scheduled binding includes schedulerId, workflowId/version, timezone, cadence/trigger, enabled, destination bindings and last observed run. Publish "configured" only after schedule readback, and "ran successfully" only after execution evidence.
Task-focus conversational behavior can operate without a scheduler. External document watching requires an actual authenticated event source and deduplication storage. Existing schedules must be searched before creating a new one.
Example: changing the shift prompt preserves its existing 07:00/15:00/23:00 America/Los_Angeles cadence and enabled state unless requested otherwise. The scaffold's manual-only MVP does not disable an independently existing workspace automation.
Acceptance: instruction update does not silently enable; rerun does not duplicate schedules; unavailable scheduler reports blocked; rejected capability remains unavailable regardless of skill wording.

