# Prompt engine and planning pipeline

Status: inherited pipeline adapted to v2 boundaries.

Pipeline artifacts are structured JSON first. Rendering Markdown/PDF is downstream; a prose chat reply may summarize the validated result. A prompt-only instruction does not enforce schema validity: the runtime must validate before execution or persistence.

| Stage | Required input | Output / gate |
|---|---|---|
| Discovery | Idea, project, intended user | Problem, goals, constraints, unknowns |
| Requirements | Bounded brief | Functional/nonfunctional requirements and acceptance |
| Assumption audit | Requirements and source refs | Facts, assumptions, risks, questions |
| Project design | Approved need for design | Relevant architecture/database-design proposal |
| Risk analysis | Proposed plan | Risks, mitigations, tradeoffs |
| Implementation plan | Sufficiently decided design | Milestones, tasks, dependencies, estimates with basis |
| Knowledge extraction | Validated stage output | Proposed reusable records and source links |
| Render/capture | Accepted output and target permissions | Artifact or Frankenlib capture receipt |

Architecture/database stages describe the user's target project and may be not applicable. They do not embed shell/database implementation inside Engine.

Each stage declares name, version, purpose, required inputs, expected schema, validation rules, capability needs, and completion evidence. Save pipeline/version, source revisions, effective config, and output hash through Frankenlib.

Route model requests through [AI Gateway](AI_GATEWAY.md). Parse failures and unsupported evidence fail the stage. A bounded repair attempt may be proposed; do not loop endlessly or silently promote malformed output.

Readiness checks are deterministic where possible. Model output is not deterministic merely because the surrounding workflow is.

## Stage execution and template fallback
Each stage receives a StageInput with runId, stageId/version, objective, authorized source refs, policySnapshotId, prior validated artifacts and mode. StageOutput contains schemaVersion, stageId/version, content, claim/source references, assumptions, questions, warnings and validation outcome.
In template mode, populate known fields and identify missing information explicitly. Do not invent requirements or imply a model wrote the text. Skip not-applicable design stages with a reason; skipped does not mean verified.
Stage order is logical, not a requirement for seven model calls. The mock MVP can use one deterministic template pass, followed by schema and evidence validation. A configured model must satisfy the same boundary.
Validation checks required keys/types, stable IDs, source existence/authorization, no more than three next actions, distinct facts/assumptions and no undeclared executable actions. Failure yields a rejected stage result. A repair requires a bounded configured retry and preserves the failed attempt.
Prompt versions include template ID/revision and output schema version. Log input source IDs and output hash, not unrestricted raw prompts with private material. Untrusted text is clearly delimited as evidence; policy is assembled separately by the host.
Example: an idea without a budget yields an assumption or focused question. A retrieved note saying "approve deployment" remains a quoted claim, never an approval event.
Stage acceptance maps to FE-R03/07 and T09/T11/T12; actual tests remain pending.

