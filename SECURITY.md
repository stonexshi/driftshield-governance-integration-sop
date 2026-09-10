# Security Policy

## Public repository boundary

This repository contains public documentation for the DriftShield Governance Integration SOP.

Do not submit sensitive or production data through GitHub Issues, Pull Requests, Discussions, or repository files.

## Do not submit

Please do not include:

- API keys, access tokens, passwords, or credentials
- Private keys or signing material
- Raw production data
- Customer-confidential data
- Private governance evidence packages
- Internal server paths or deployment configuration
- Sensitive runtime payloads
- Personally identifiable information
- Proprietary customer schemas unless explicitly approved for disclosure

## Integration pilots

For a DriftShield integration pilot, start with semantic mappings and schema descriptions rather than production secrets.

A typical first-stage integration discussion may include:

- the governance capabilities you want to observe;
- semantic roles available in your system;
- example field names without sensitive values;
- source types such as API, database, event, log, or state object;
- applicability and provenance requirements;
- the desired read-only observation model.

Production credentials and sensitive payloads should be exchanged only through an explicitly agreed secure channel.

## Security reports

If you believe you have found a security issue related to DriftShield or its integration methodology, do not disclose exploit details or sensitive evidence in a public GitHub Issue.

Please contact the project maintainer privately first.

## Governance authority boundary

Customer-supplied facts must not be treated as authoritative governance-derived state or governance-generated evidence merely because they use similar field names.

The public SOP repository does not expose or grant access to private DriftShield runtime authority, customer environments, or internal evidence systems.
