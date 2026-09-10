# Customer Data Responsibility Contract

Version: v0.1.2

Release: Public

## 1. Contract purpose

This contract defines who supplies facts, who owns governance authority, and how absence is handled.

The four classes below are the base responsibility taxonomy.

Applicability, fallback, and cardinality do not create additional base responsibility classes.

## 2. Base responsibility classes

| Responsibility class | Provider | Authority | Customer mapping rule | Governance rule | Absence behavior |
|---|---|---|---|---|---|
| `CUSTOMER_REQUIRED` | `CUSTOMER_SYSTEM` | `CUSTOMER_FACT` | BIND_CUSTOMER_SOURCE_WHEN_SELECTED_CAPABILITY_AND_APPLICABILITY_REQUIRE_ROLE | VALIDATE_AND_CONSUME_AS_CUSTOMER_FACT_NOT_AS_GOVERNANCE_STATE | FAIL_OR_HOLD_WHEN_APPLICABLE_REQUIRED_ROLE_IS_UNBOUND |
| `CUSTOMER_OPTIONAL` | `CUSTOMER_SYSTEM` | `CUSTOMER_FACT` | MAY_BIND_CUSTOMER_SOURCE_BY_CUSTOMER_MAPPING_CONTRACT | DO_NOT_PROMOTE_ABSENCE_OR_OPTIONAL_METADATA_TO_GOVERNANCE_AUTHORITY | MAY_BE_ABSENT_UNLESS_CUSTOMER_CONTRACT_EXPLICITLY_OVERRIDES |
| `GOVERNANCE_DERIVED` | `GOVERNANCE_SYSTEM` | `GOVERNANCE_DERIVED_STATE` | NOT_CUSTOMER_INPUT | DERIVE_FROM_BOUND_FACTS_EVIDENCE_AND_GOVERNANCE_AUTHORITY | NOT_APPLICABLE_AS_CUSTOMER_INPUT |
| `GOVERNANCE_GENERATED` | `GOVERNANCE_SYSTEM` | `GOVERNANCE_GENERATED_STATE_OR_ARTIFACT` | `NOT_CUSTOMER_INPUT` | GENERATE_CANONICAL_GOVERNANCE_IDENTITIES_READ_ONLY_LOCATORS_AUDIT_EVIDENCE_REPLAY_REPORT_RECEIPT_OR_EQUIVALENT_STATE_OR_ARTIFACTS_AS_IMPLEMENTATION_REQUIRES | `NOT_APPLICABLE_AS_CUSTOMER_INPUT` |

## 3. Authority rules

### CUSTOMER_REQUIRED

The customer supplies the factual input when the selected capability and applicability contract require it.

The governance layer validates and consumes the fact.

The customer does not thereby gain governance-state authority.

### CUSTOMER_OPTIONAL

The customer may supply the fact.

Absence is allowed unless the customer-specific mapping contract explicitly changes the obligation.

Optional customer metadata cannot silently become governance authority.

### GOVERNANCE_DERIVED

The governance system computes the state from admissible facts, evidence, and governance authority.

The customer cannot submit this class as authoritative governance state.

### GOVERNANCE_GENERATED

The governance system creates governance-generated state or artifacts whose authority belongs to the governance system.

For a long-term governance observation, this class includes:

- the canonical long-term governance identity;
- each per-session governance identity;
- the stable read-only Control Room locator bound to the long-term governance identity;
- evidence, audit records, receipts, reports, replay links, hashes, and equivalent implementation-specific artifacts.

The governance system, not the customer, owns generation and canonical binding of the long-term governance identity.

A customer-supplied execution, workflow, continuity, correlation, account, or similarly named identifier may remain customer fact or mapping context, but it cannot become the canonical long-term governance identity merely because its value or name resembles a governance-generated identity.

The customer may receive, display, retain, or use the system-assigned long-term identity and read-only Control Room locator for observation, but those actions do not grant authority to select, replace, rotate, or rebind the canonical identity.

A new governance session may receive a new governance-generated session identity while remaining under the existing long-term governance identity.

The customer cannot forge or supply governance-generated identities, locators, or artifacts as authoritative governance outputs.

## 4. Modifier dimensions

### APPLICABILITY

REQUIREDNESS_IS_EVALUATED_ONLY_WHEN_THE_SELECTED_CAPABILITY_AND_CUSTOMER_MAPPING_CONTRACT_DECLARE_THE_ROLE_APPLICABLE

### FALLBACK

FALLBACK_MAY_BE_USED_ONLY_WHEN_EXPLICITLY_DECLARED_BY_THE_GOVERNANCE_INPUT_MAPPING_CONTRACT_AND_MUST_NOT_CHANGE_CUSTOMER_FACT_AUTHORITY

### CARDINALITY

ROLE_CARDINALITY_IS_IMPLEMENTATION_DEFINED_AND_CAPABILITY_DEPENDENT_AND_MUST_NOT_BE_COPIED_FROM_THE_REFERENCE_IMPLEMENTATION

## 5. Customer deployment rule

A customer deployment shall classify every selected semantic role into exactly one base responsibility class.

Applicability, fallback, lifecycle conditions, and multiplicity must be recorded separately.

When long-term governance observation is part of the selected capability, the deployment shall preserve the following responsibility boundary:

- the governance system generates and owns the canonical long-term governance identity;
- the governance system generates each governance session identity;
- the governance system binds and exposes the stable read-only Control Room locator;
- the customer is not required to design or supply the canonical long-term governance identity;
- the initial supported handoff surfaces the system-assigned long-term identity and its stable Control Room locator;
- the supported handoff explicitly instructs the customer to save or retain the long-term identity and Control Room locator;
- customer retention of the identity or locator is an operational handoff responsibility and does not grant governance authority;
- redisplaying an existing long-term identity or locator must not generate a replacement canonical identity.

The exact customer-facing wording, identity string format, and locator shape are implementation-defined.

This contract does not require username/password recovery, SSO recovery, account mapping, or forgotten-URL recovery.

## 6. Fail-closed boundary

If responsibility ownership is ambiguous, the integration must hold rather than silently assign governance authority.

If canonical long-term identity ownership or its binding to the read-only Control Room locator is ambiguous, the integration must hold rather than:

- accepting a customer-supplied identifier as canonical authority;
- replacing an existing long-term governance identity;
- rebinding existing history to another long-term governance identity;
- guessing which long-term identity or locator should be returned.
