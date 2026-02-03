# Policy Revocation List (PRL) — Normative

A Policy Revocation List (PRL) defines policies that MUST be rejected by a verifier,
even if they are correctly signed.

## Format
A PRL MUST be a JSON object:

{
  "version": "1.0.0",
  "issuer": string,
  "revoked_policies": string[]
}

## Semantics
- A PRL MUST be signed by the same authority as policies.
- A verifier MUST reject a policy if its policy_id appears in revoked_policies.
- Revocation is absolute and offline.
- No timestamp interpretation is permitted.

## Verification Order
1. Verify policy signature (A15)
2. Verify PRL signature
3. Apply revocation check (A16)
