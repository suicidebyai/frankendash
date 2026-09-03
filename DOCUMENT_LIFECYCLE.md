# Document lifecycle and index synchronization

Status: workflow specification; no external records changed by this file.

## Identity and authority

Resolve the owning project and existing canonical artifact first. Match stable source ID plus project/type; for repository files use repository/path, with commit as revision. Title-only matching is insufficient.

Lifecycle values: draft, approved, superseded, archived. Verification and synchronization status are independent fields. Archived/superseded records remain traceable unless deletion is explicitly authorized.

Use the current project index as a source map, not a universal authority for every field. GitHub owns committed repository content; Drive may own a working draft; Asana owns operational task state; Frankenlib owns runtime persistence. Follow approved domain ownership.

## Procedure

1. Search/read the artifact and its existing index record; disambiguate before writes.
2. Create or minimally update the authorized source.
3. Read back source identity, revision, content, and canonical location.
4. Update the owning subsystem index with title, type, project, location, lifecycle, authority, revision, reviewedAt, and related tasks/decisions.
5. Upsert the structured registry, preserving human notes and external IDs.
6. Update the master index only for cross-system relationships, integration milestones, or changed navigation.
7. Update relevant operational tasks and the active shift report with verified outcomes and links.
8. Read back each required destination and record its result.

Never flatten Frankendash, FrankEngine, and Frankenlib indexes into a replacement master file. The master index is navigation and relationships, not a competing store of all subsystem content.

## Partial failure and replay

Per destination: not_attempted, unchanged_verified, updated_verified, blocked, conflict, failed, or outcome_unknown. Overall success requires every required destination verified; otherwise report partial/blocked.

Keep source revision and failed step for retry. Read target state before replay. Do not repeat a successful create, overwrite a newer human edit, or treat an unavailable system as unchanged.

Temporary local links are useful downloads, not permanent external index locations. Register durable canonical links after saving.

## Research capture

“save to lib,” “auto-tag and categorize,” “auto -t -c,” and “auto -a” select the relevant preceding material. Read the current research protocol before assigning one primary category and minimal controlled tags. Do not invent taxonomy when its source is unavailable.

Frankenlib owns classification/storage capability; Engine orchestrates the capture, uncertainty handling, and downstream registration.

## Concrete reconciliation example and completion rule
Example: update an existing FrankEngine spec. Resolve its Drive file ID and module owner; read current bytes/revision; prepare a minimal change; update that same ID; fetch and compare saved contents. Update the local V2 index, existing parent index, registry mapping and active shift/task references required by the request.
Registry key: owning project + source system + stable source ID + artifact type. A revision updates that record; it is not a new artifact. Same title in Frankendash and FrankEngine remains two different records.
If Drive succeeds but Airtable fails, retain the saved source revision, mark registry pending and retry only that mapping after fetching current state. Do not recreate the source, mark combined sync done, or overwrite newer human notes.
Document lifecycle and sync result remain separate. A reviewed draft can be synced but unapproved; an approved spec can be incompletely mirrored. Readback verifies the contents promised by this operation, not unrelated product behavior.
Host orchestration owns sequencing and adapter execution; Frankenlib owns runtime records/indexing; external system authority is respected for its record classes. The existing workspace workflow is not silently replaced by a new Engine runtime.
Acceptance: twice-run update yields one artifact/mapping; wrong-project title match never merges; content mismatch blocks completion; partial failure retains precise retry pointers.

