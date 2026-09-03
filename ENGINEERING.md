# Engineering and contribution rules

Status: v2 adaptation of source ENGINEERING; no build system installed.

Read README, boundaries, constitution, decisions, contracts, and acceptance before changes. Keep one source of truth for each rule; link from other docs instead of forking definitions.

Use small, purposeful changes. Preserve existing work. New dependencies need a concrete problem, alternatives, maintenance/cost impact, and permission review. Do not introduce UI, ORM, SQL, or provider-specific SDK dependencies into workflow policy.

TypeScript, pnpm, and Vitest are inherited candidates. Pin versions only after the runtime implementation decision. Do not publish nonworking install/build commands.

A future implementation should isolate deterministic policy tests from model output and external adapters. Unit tests cover validation/routing; integration tests cover workflow recovery and ports; client tests belong to Frankendash; storage tests belong to Frankenlib.

Repository changes require an explicitly approved target and review workflow. This documentation pack does not authorize branch creation, pushing, or merging. Do not reuse a quarantined historical branch without fresh instruction.

A contribution includes context, changed behavior, source/decision links, acceptance evidence, risk/recovery notes, and updated docs. Never commit credentials or private operational source maps.

No separate DEVELOPMENT/CONTRIBUTING files are needed until they contain unique setup or contribution requirements not covered here.

## Build-ready handoff requirements
This pack is a complete review draft, not a runnable repository. Do not invent package.json, lockfile, command output or version numbers. Choose the runtime and exact review target under FE-O01 before initialization.
Recommended implementation order: shared data contracts and validators → host composition → deterministic reasoning/policy → in-memory Frankenlib fixture → blueprint review/export loop → real Frankenlib durability/recovery → optional provider → one connector workflow. This aligns ROADMAP and PRODUCT_SPECIFICATION.
For each change, record owning layer, affected contract version, migration impact, acceptance fixtures and recovery. Preserve exported names until a documented compatibility revision. Keep database-specific tests inside Frankenlib; test its public port from host integration tests.
The eventual verification entrypoints must cover schema validation, deterministic fixtures, module import boundaries, durable acceptance/idempotency, source/export parity and secret redaction. Document real install/test/start commands only after they exist and have been run.
Use fixture IDs and fake credential references in examples. Operational source-map IDs belong in private configuration; portable docs may link public ownership sources but should not embed private session material.
Review completion: all relative links resolve within the pack or identify an external source, examples match the proposed contracts, requirements have checks, and unresolved decisions have an owner/next action. Runtime test completion remains separately unverified.

