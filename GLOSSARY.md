# Glossary

FrankEngine: behavior, reasoning, decision, and orchestration system.
Frankendash: workspace shell and interaction presentation.
Frankenlib: persistent knowledge, retrieval, search/indexing, and relationships. D.libber is historical.
AI Gateway: provider-neutral model invocation boundary.
Artifact: document or other deliverable with explicit lifecycle and source authority.
Knowledge Object: versioned reusable information managed by Frankenlib.
Blueprint: structured plan composed of requirements, decisions, risks, and tasks.
Function: bounded callable operation.
Skill: reusable instructions and capability-selection guidance.
Workflow: versioned sequence with state and gates.
Automation: configured event/schedule execution of a workflow.
Run: one workflow instance, with attempts, events, effects, and evidence.
Effect: a read/write action against a system; writes require scoped permission.
Evidence: inspected source/revision/result supporting a claim.
Canonical: authoritative for a particular record class, not globally authoritative for everything.
Mirror: derivative copy whose authority is explicitly subordinate.
Verified: checked against declared criteria.
Synced: required destination revisions checked, not merely attempted.
Ready: readiness checks passed; not implicit implementation permission.
Parking lot: preserved future work outside active scope.

## Current terminology — supersedes abbreviated ownership above
| Term | Precise meaning |
| --- | --- |
| FrankEngine | Backend host containing modules and shared execution/integration services |
| AI Reasoning | FrankEngine module for interpretation, behavior, scope, custom instructions and workflow decisions |
| Frankenlib / flib | FrankEngine module for durable state, source records, search, indexing, taxonomy and provenance |
| Shared host service | API/session, composition, connector, configuration or credential-provider boundary used by modules |
| Library port | Public in-process contract; not permission to access private storage tables |
| Template mode | Structured non-model output using known inputs and explicit gaps |
| Mock adapter | Test fixture implementation; does not prove real durability or remote effects |
| Acceptance | User decision about an exact blueprint revision/hash |
| Effect authorization | Permission for an exact action/target; separate from blueprint acceptance |
| Verified draft | Document content/readback checked; implementation remains unproven |
| Complete sync | Every required target has confirmed readback at the relevant source revision |
Defaults remain a policy document and resolution concern, not a new module. D.libber remains a historical alias only. Module ownership does not merge or delete the existing project folders/indexes.

