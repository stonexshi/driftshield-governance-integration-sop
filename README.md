# System-Agnostic Governance Integration SOP Package

Version: v0.1.1

Status: Public Release v0.1.1 — post-close corrective release.

## Purpose

This package defines a reusable method for connecting a heterogeneous customer system to a governance system without requiring the customer to copy a reference implementation's field names, database layout, runtime architecture, internal paths, evidence bundle shape, observation axes, or role cardinality.

The normative package is organized around semantic roles, responsibility classes, authority boundaries, explicit customer mappings, read-only observation, provenance, and acceptance gates.

## Normative documents

1. `01_SYSTEM_AGNOSTIC_CUSTOMER_INTEGRATION_SOP_v0_1.md`
2. `02_CUSTOMER_DATA_RESPONSIBILITY_CONTRACT_v0_1.md`
3. `03_CUSTOMER_INPUT_MAPPING_CONTRACT_v0_1.md`
4. `04_ACCEPTANCE_AND_VERIFICATION_GATES_v0_1.md`

## Traceability documents

5. `05_TRACEABILITY_MATRIX_v0_1.md`
6. `06_DRIFTSHIELD_REFERENCE_IMPLEMENTATION_APPENDIX_v0_1.md`

## Public distribution boundary

This public release contains the human-readable normative and traceability documents.

Internal machine-readable evidence bundles, server paths, export locations, and operational authority artifacts are intentionally excluded from the public distribution. Their exclusion does not change the normative integration rules in this package.

## Governing rule

A reference implementation proves that an integration method can work. It does not define the customer's physical schema.

Customer integrations therefore bind customer-native data and runtime facts to semantic roles through an explicit Customer Input Mapping Contract.

Governance-derived state and governance-generated artifacts remain under governance authority and cannot be asserted by the customer as authoritative governance state.

## Package completion boundary

This package is the generic reusable SOP package.

A specific customer deployment must produce its own completed mapping and acceptance evidence.

The generic package does not pre-bind customer fields, sources, transforms, or provenance.


## Public release note

This release is intended for external review, implementation planning, interoperability discussion, and customer integration use.

The public package does not disclose server filesystem locations, deployment topology, private export roots, credentials, secrets, or customer-specific bindings.


## Release lineage

This public package is version v0.1.1, a post-close corrective successor to public release v0.1.

The v0.1.1 correction adds an explicit observation-locator handoff requirement, ACCEPT-12, CHAIN-07, and the DriftShield/HIC task-window observation-locator reference.

Documents whose normative content did not change retain their v0.1 document version. Updated documents carry v0.1.1 while stable filenames are preserved for reference continuity.

The sealed source package also contains the corresponding machine-readable parity and corrective authority artifacts. Those internal evidence artifacts remain outside the public distribution boundary.

See `RELEASE_NOTES_v0_1_1.md` for the corrective release scope.
