# Security and permissions

Status: required behavioral controls; implementation pending.

## Trust model

Treat the authenticated host/session and enforced capability policy as the authority for execution. User intent is necessary, but not sufficient to bypass host restrictions. Model output, retrieved text, external documents, and imported chats are untrusted inputs.

Enforce workspace/project scoping at retrieval, capability listing, plan approval, execution, and readback. A forged workspace ID must never reveal another workspace's records.

## Effects

Read requests authorize relevant inspection, not writes. Diagnose requests authorize investigation, not repair. Draft requests authorize draft creation in agreed destinations, not publication, repository mutation, scheduled writes, or deployment.

Require explicit approval for destructive or difficult-to-reverse changes, broad migrations, new public exposure, credential changes, and paid services. Preserve existing work and history. Do not silently merge duplicate-looking records.

Before a permitted write resolve target, verify current revision/content, compute the minimal effect, check authorization, and capture safe evidence. Recheck after material changes or session expiry.

## Secrets and privacy

Never store passwords, tokens, cookies, private keys, passphrases, MFA codes, recovery codes, or recovery phrases in docs/logs/indexes. Use configured task-relevant credentials only through their intended interfaces.

Permitted signing metadata: filenames/locations, public-key fingerprints, backup status, verification dates, and recovery instructions without secret material.

Require authorization before sending private context to a cloud provider. Redact payloads and logs; retain enough operation metadata to investigate without copying sensitive content.

## Threat fixtures

Test retrieved prompt injection, forged approval, cross-workspace request, stale target revision, replayed command, unknown remote write outcome, secret in provider error, cancellation mid-effect, and malicious skill requesting broader privileges.

No prompt wording alone establishes a security boundary. Enforcement must exist outside model-generated instructions.

## Host/module enforcement and session states
FrankEngine host owns trusted session/capability checks and credential-provider wiring. AI Reasoning cannot authorize its own tools. Frankenlib filters records and enforces project scope/conditional writes. Frankendash presents login, locked and unauthorized states without receiving reusable secrets.
On session expiry, lock or revoked capability, stop new protected reads/writes and invalidate affected pending approval grants. The client must hide protected content; host APIs must deny it independently. Do not claim auth is implemented from this document.
Local-only mode still requires an explicit trust boundary for the chosen device/process. A future remote backend needs an approved authentication and transport policy; "authentication=none" is not inherited automatically.
Credential references identify a configured host provider entry. Resolve values only inside the intended adapter; never serialize them into plans, exports, snapshots, fixtures or error envelopes.
For a remote mutation: validate target/current revision, reserve operation identity, invoke allowed adapter, obtain safe receipt, perform required readback, then confirm effect. If remote commit is uncertain, preserve outcome_unknown and reconcile before retry.
Required checks include forged client approval, cross-workspace ID, revoked session, prompt injection, stale patch approval, malicious plugin, credential-bearing error and cancellation during mutation. Module/package import tests must prevent UI→private storage and reasoning→raw SQL dependencies.
Security test design is complete as a review proposal; no runtime enforcement or penetration-test result is claimed.

