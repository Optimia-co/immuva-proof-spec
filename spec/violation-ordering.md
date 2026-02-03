# Violation Ordering (Normative)

This document defines the deterministic ordering of `violations` emitted by a verifier.

## Rule

When a verifier emits multiple violations, the `violations[]` array MUST be ordered
according to the canonical order defined below.

Verifiers MUST NOT emit duplicates.

## Canonical Order (Policy Layer)

1. MIN_PROOF_LEVEL_NOT_MET
2. KEY_BINDING_REQUIRED
3. TIME_ANCHOR_REQUIRED
4. TRANSPARENCY_LOG_REQUIRED

Notes:
- If A9.2 precedence short-circuits (min_proof_level failure), violations MUST contain ONLY:
  - MIN_PROOF_LEVEL_NOT_MET
