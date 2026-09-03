# AI Gateway

Status: proposal consistent with source provider-agnostic direction.

Expose a provider-neutral invocation receiving request ID, model capability requirements, prompt version, authorized context, output schema, cancellation signal, and budget constraints.

Return provider/model/version metadata, normalized output, usage where available, finish reason, and normalized error. Never expose raw credentials in results.

No provider is selected by default. Mock mode supports offline verification. A local model is preferred where practical; a cloud provider requires user configuration and accepted cost/data handling. Do not infer that an existing chat subscription grants free API use.

Before invocation check provider availability, approved context sharing, cost ceiling, and cancellation. Do not silently fall back from local to cloud or switch to a paid model.

Normalize unavailable provider, context limit, rate limit, timeout, refusal, malformed output, and cancellation. Preserve refusals rather than bypassing them via provider hopping. Retry transient calls only within [defaults](../core/DEFAULTS.md); tool-writing workflows remain independently gated.

Provider-specific SDKs stay behind adapters. SDK versions and deployment are not selected here.

## Invocation shape and operating modes
Request: invocationId, runId, promptVersion, policySnapshotId, mode, providerRef when applicable, messages/content segments with source IDs, outputSchemaVersion, context-sharing scope, timeout/cancellation and budgetPolicyRef.
Modes: template (no model), mock (fixture output), local (configured local model), cloud (explicitly configured and authorized remote model). Return the actual mode; never silently upgrade template/local to cloud. A missing provider is a supported template state.
Response: invocationId, actual mode, provider/model identity when used, validated structured output or safe error, finish reason, usage with known/unknown fields, evidence references and warnings. Never fabricate cost or token usage where unavailable.
Default automatic retry count for this proposal is zero until an explicit bounded retry policy is configured. A caller may retry a transient read/generation within that policy; never repeat an external mutation through model generation. No infinite JSON-repair loop.
On timeout/cancel/refusal/malformed output, retain safe run metadata and return failure without accepting a blueprint. If stream output is later supported, partial tokens remain unvalidated presentation until the final schema check.
Acceptance: template and mock modes make no network call; local failure does not invoke cloud; private context not approved for sharing stays local; malformed output cannot trigger a capability; errors redact credentials. Provider SDK and runtime versions are selected at implementation review.

