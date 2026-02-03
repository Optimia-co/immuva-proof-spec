# Policy (Normative)

A Policy defines declarative verification constraints applied by a verifier.

## Policy Object
A policy MUST be a JSON object with the following fields:

- version: string (required)
- min_proof_level: ProofLevel (optional)
- require: object (optional)
  - key_bound: boolean
  - time_anchor: boolean
  - transparency_log: boolean

## Semantics
- Policies are evaluated AFTER cryptographic verification.
- If min_proof_level is set, it MUST be enforced first (A9.2 precedence).
- require.* constraints are enforced only if min_proof_level passes.

## Overrides
- If a policy is provided, it takes precedence over CLI flags.
- CLI flags MAY override policy only if explicitly enabled by the verifier.

## ProofLevel Ordering
BASIC < KEY_BOUND < TIME_ANCHORED < TRANSPARENCY_LOGGED

## Signing & Canonicalization (A12)

Policies MUST be signed over their canonical JSON representation.

- Canonicalization is defined by the Immuva Canonical JSON rules.
- Canonicalization is performed independently by:
  - the signer
  - the verifier
- A policy signature MUST be verified before policy enforcement.
- The user MUST NOT manually canonicalize policies.

Note: The reference CLI command `immuva policy sign` is defined but may not be implemented yet.
