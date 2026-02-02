# Cryptographic Suites Registry (Normative)

This section defines the canonical registry of cryptographic suites
supported by Immuva Proof v1.x.

## General Rules

- A `crypto_suite` identifier MUST be explicitly declared when signing.
- Unknown `crypto_suite` values MUST result in verdict INVALID.
- Each suite defines:
  - signature algorithm
  - hashing semantics
  - key requirements

## Supported Suites

### IMMUVAv1-SHA256

- Signature = hex(sha256(canonical_event))
- No public key
- Compatibility-only
- NOT suitable for non-repudiation

### IMMUVAv2-ED25519-SHA256

- message_hash = sha256(canonical_event)
- signature = Ed25519(message_hash)
- Public key REQUIRED
- Deterministic, non-malleable

## Backward Compatibility

Implementations MUST preserve IMMUVAv1 semantics.
IMMUVAv2 is strictly opt-in and MUST NOT affect legacy validation.

