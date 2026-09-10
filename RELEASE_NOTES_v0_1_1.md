# DriftShield Governance Integration SOP v0.1.1

Version: v0.1.1

Release class: Post-close corrective release

Parent release: v0.1

## Corrective scope

- Adds an explicit execution/session identity and read-only observation-locator handoff requirement.
- Adds `ACCEPT-12` for observation-locator return and execution binding.
- Adds `CHAIN-07` to both human-readable and machine-readable traceability surfaces.
- Documents the DriftShield/HIC reference mapping from `task_window_id` to the read-only Governance Control Room locator.
- Keeps `write_token` outside the read-only observation locator.
- Preserves the original v0.1 sealed package, closed-phase traceability, and prior authority ledger without mutation.

## Versioning note

Unchanged normative documents retain version v0.1. Documents changed by this corrective release carry version v0.1.1. Existing filenames remain stable to preserve reference continuity.

## Runtime boundary

This corrective release changes documentation, acceptance parity, traceability, and publication metadata only. It does not modify the DriftShield/HIC product runtime.
