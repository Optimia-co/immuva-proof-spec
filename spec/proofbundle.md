# Immuva ProofBundle Specification
Version: 1.0  
Status: **Normative**  
Last updated: 2026-01-30

---

## 1. Scope

This document defines the **normative specification** for the Immuva ProofBundle format.

A ProofBundle is a **self-contained, deterministic, cryptographically verifiable evidence package** designed to prove that an autonomous system action occurred.

This specification is implementation-agnostic.

---

## 2. Design Goals

A compliant ProofBundle MUST be:

- Self-contained (no external dependency required for verification)
- Deterministic (byte-for-byte reproducible)
- Cryptographically verifiable
- Tamper-evident
- Offline-verifiable

---

## 3. Canonical Structure

A ProofBundle MUST be either:
- a directory, or
- a deterministic ZIP archive

With the following canonical structure:

proofbundle/
├── events.jsonl
├── hashes.json
├── signature.json
├── anchor.json (optional)
├── redaction_report.json (optional)
└── artifacts/ (optional)

yaml
Copier le code

File names and paths are **case-sensitive**.

---

## 4. events.jsonl (Event Chain)

- Append-only
- One JSON object per line
- Each event MUST include:
  - timestamp
  - event_type
  - payload_hash
  - previous_event_hash

Events MUST be cryptographically chained.

Any modification invalidates the chain.

---

## 5. hashes.json (Integrity Manifest)

This file MUST list:

- file path
- byte size
- SHA-256 hash

All files except `signature.json` MUST be included.

Order MUST be lexicographical.

---

## 6. Root Hash

The root hash is computed as:

root_hash = SHA256(concat(path | size | sha256))

yaml
Copier le code

This value represents the immutable commitment of the ProofBundle.

---

## 7. signature.json (Cryptographic Seal)

This file MUST include:

- root_hash
- signature_hex
- algorithm (Ed25519)
- public_key_hex
- created_at
- proof_level (array)

Optional fields:
- certificate
- anchor

The signature MUST cover the root hash.

---

## 8. Proof Levels

Proof levels indicate assurance strength:

| Level | Guarantee |
|------|----------|
| VALID | Integrity & immutability |
| KEY_PROTECTED | Secure signing environment |
| TIME_ANCHORED | Independent timestamp |
| CERTIFIED_IMMUVA | Certified identity |

Proof levels MUST be explicitly declared.

---

## 9. Deterministic ZIP Requirements

If zipped:
- No timestamps
- Stable file ordering
- Fixed compression
- Byte-for-byte reproducibility REQUIRED

---

## 10. Verification

Verification MUST:

1. Recompute file hashes
2. Recompute root hash
3. Verify signature
4. Verify event chain
5. Validate proof levels
6. Enforce revocation (if applicable)

Verification is deterministic.

---

## 11. Security Model

ProofBundles provide:

- Integrity
- Non-repudiation
- Temporal ordering

They do NOT:
- Validate business logic
- Prevent incorrect decisions
- Detect omitted actions

---

## 12. Conformance

An implementation is compliant if it produces ProofBundles that satisfy all MUST requirements in this document.

---

End of specification.
