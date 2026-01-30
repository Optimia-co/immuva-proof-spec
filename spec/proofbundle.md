# Immuva ProofBundle Specification

## Overview

An Immuva ProofBundle is a deterministic, verifiable container
that encapsulates cryptographic evidence of autonomous actions.

A ProofBundle is self-contained and verifiable without access
to Immuva infrastructure.

---

## Design Goals

- Deterministic verification
- Offline auditability
- Minimal data exposure
- Tamper evidence
- Zero-trust verification

---

## Bundle Forms

A ProofBundle MAY be:

- a directory
- a deterministic ZIP archive (`.proofbundle`)

Both forms MUST produce identical verification results.

---

## Directory Structure

proofbundle/
├── events.jsonl
├── hashes.json
├── signature.json
└── artifacts/ (optional)

yaml
Copier le code

---

## events.jsonl

Append-only list of events in JSON Lines format.

Each event MUST include:
- `event_id`
- `timestamp`
- `type`
- `data_hash`
- `prev_event_hash`

Events MUST be chained by `prev_event_hash`.

Any modification invalidates the entire chain.

---

## hashes.json

List of files included in the bundle with their integrity metadata.

Each entry MUST include:
- `path`
- `sha256`
- `size`

All files except `signature.json` MUST be listed.

---

## signature.json

Cryptographic seal of the ProofBundle.

MUST include:
- `root_hash`
- `signature_hex`
- `algorithm`
- `proof_level`

OPTIONAL fields:
- `public_key_hex`
- `certificate`
- `anchor`
- `key_protected`

The signature MUST be computed over the `root_hash`.

---

## Root Hash Computation

The `root_hash` MUST be computed as follows:

1. Deterministically order `hashes.json`
2. Concatenate entries
3. Apply SHA-256

The exact procedure MUST be documented and reproducible.

---

## Deterministic ZIP Rules

When archived:
- File order MUST be deterministic
- Timestamps MUST be zeroed
- Compression MUST be deterministic
- No extra metadata allowed

ZIP output MUST be byte-for-byte reproducible.

---

## Verification Algorithm (High Level)

Verification MUST perform:

1. Event chain validation
2. File hash verification
3. Root hash recomputation
4. Signature verification
5. Proof level checks
6. Revocation checks (if applicable)

Verification results are binary:
- valid
- invalid
- revoked

---

## Security Considerations

- ProofBundles do not validate business logic
- ProofBundles do not prevent omission of actions
- ProofBundles rely on correct integration

These limitations are explicit and documented.

---

## Extensibility

Additional artifacts MAY be included
if they do not affect verification.

Verification MUST ignore unknown files
not listed in `hashes.json`.

---

## License

This specification is licensed under Apache 2.0.
