# Release Notes — v0.1.2

Status: Public Release

## Scope

v0.1.2 extends the v0.1.1 system-agnostic governance integration package with explicit long-term governance observation continuity.

The release preserves the existing customer-data mapping model while adding governance-owned long-term identity, per-session identity, stable read-only observation access, ordered successor continuity, cross-session preservation, and customer handoff requirements.

## Long-term governance identity

For each accepted long-term observation instance, the governance system generates and owns one canonical long-term governance identity.

The customer and normal public caller do not select, supply, replace, rotate, or rebind that canonical identity.

Normal creation of a new governance session does not create a new long-term observation identity.

## Governance session continuity

Each new governance observation session receives its own governance-generated session identity.

Session identity may rotate while the canonical long-term governance identity remains unchanged.

The first session is the root. Each later session is an explicit ordered successor under the same long-term governance identity.

Continuity is not established merely by timestamp order.

## Stable read-only Control Room access

The governance system exposes a stable read-only Control Room locator bound to the canonical long-term governance identity.

Session rotation, successor append, history growth, and trajectory growth do not change that locator for the same long-term observation.

The customer-facing read-only locator contains or requires no governance write credential.

## History and trajectory preservation

Prior sessions and recorded events remain part of the long-term observation history after successor sessions are appended.

A session with recorded events but no valid trajectory point remains preserved in session history; missing trajectory data does not authorize deletion or synthetic trajectory promotion.

Valid governance trajectory points may accumulate across successor sessions while preserving session linkage and successor order.

## Customer handoff

The supported initial handoff surfaces the system-assigned long-term governance identity and the stable Control Room URL.

The customer is explicitly instructed to save or retain that identity and URL for future access.

This first-version handoff does not introduce username/password recovery, SSO recovery, account mapping, or forgotten-URL recovery requirements.

## Customer mapping boundary

Customer execution, workflow, continuity, correlation, account, or similarly named identifiers remain customer facts or mapping context unless another contract gives them a separate customer-side meaning.

A customer runtime identifier does not become the canonical long-term governance identity or governance session identity merely because its value or name resembles a governance-generated identifier.

Canonical governance identities remain governance-generated roles and are not customer completion fields.

## Reference implementation boundary

The DriftShield/HIC reference implementation uses an `observation_stream_id` for the long-term observation and a `task_window_id` for an individual observation session.

DriftShield-specific `os_...` and `tw_...` prefixes, hexadecimal identifier shapes, query-parameter names, and Control Room URL shape are reference implementation details.

They are not universal customer integration requirements.

The release does not make any current DriftShield session count, boundary count, event count, or trajectory-point count a universal SOP requirement.

## Acceptance and traceability

The public acceptance hierarchy now runs through `ACCEPT-21`.

The public derivation hierarchy now runs through `CHAIN-13`.

The new gates and chains cover long-term identity authority, identity stability, governance session identity, ordered successor continuity, stable locator behavior, history preservation, cross-session trajectory continuity, customer handoff, and reference-format boundaries.

## Public package changes

Updated in v0.1.2:

- `01_SYSTEM_AGNOSTIC_CUSTOMER_INTEGRATION_SOP_v0_1.md`
- `02_CUSTOMER_DATA_RESPONSIBILITY_CONTRACT_v0_1.md`
- `03_CUSTOMER_INPUT_MAPPING_CONTRACT_v0_1.md`
- `04_ACCEPTANCE_AND_VERIFICATION_GATES_v0_1.md`
- `05_TRACEABILITY_MATRIX_v0_1.md`
- `06_DRIFTSHIELD_REFERENCE_IMPLEMENTATION_APPENDIX_v0_1.md`
- `README.md`

New in v0.1.2:

- `RELEASE_NOTES_v0_1_2.md`

Unchanged by this release:

- `LICENSE`
- `SECURITY.md`
- historical `RELEASE_NOTES_v0_1_1.md`

`SHA256SUMS.txt` is resealed only after the v0.1.2 candidate content has completed verification.

## Public distribution boundary

The public package remains human-readable.

Internal machine-readable parity evidence, authority artifacts, server paths, export roots, credentials, secrets, and customer-specific bindings remain outside the public distribution.

## Release lineage

v0.1.2 is a successor to v0.1.1 and does not rewrite or reopen the historical v0.1 or v0.1.1 releases.

The v0.1.1 release notes remain the historical record of the prior observation-locator corrective release.
