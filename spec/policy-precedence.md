# Policy Precedence (A18) — Normative

This section defines the precedence rules between CLI constraints and signed policies.

## Principle
A signed policy (A15) that is not revoked (A16) defines minimum constraints.
CLI flags MUST NOT weaken a policy. CLI flags MAY strengthen constraints.

## Inputs
- `policy`: the effective policy object (possibly composed) containing:
  - `min_proof_level?: ProofLevel`
  - `require.key_bound?: boolean`
  - `require.time_anchor?: boolean`
  - `require.transparency_log?: boolean`
- `cli`:
  - `--min-proof-level <ProofLevel>`
  - `--require-key-bound`
  - `--require-time-anchor`
  - `--require-transparency-log`

## Effective Constraints
Let `maxProofLevel(a,b)` return the stricter of two ProofLevels according to the canonical order.

The verifier MUST compute:

- `effective.min_proof_level = maxProofLevel(policy.min_proof_level, cli.min_proof_level)`
- `effective.require.key_bound = (policy.require.key_bound == true) OR (cli.require_key_bound == true)`
- `effective.require.time_anchor = (policy.require.time_anchor == true) OR (cli.require_time_anchor == true)`
- `effective.require.transparency_log = (policy.require.transparency_log == true) OR (cli.require_transparency_log == true)`

## Prohibitions
- A verifier MUST NOT accept a weaker effective configuration than the policy requires.
- If CLI requests a weaker configuration than the policy, the policy requirements MUST remain in effect.

## Determinism
The effective constraints MUST be computed deterministically and applied before verification.
