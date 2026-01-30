# Immuva ProofBundle Specification
Version: 1.0  
Status: Normative  
Last updated: 2026-01-30

---

## 1. Purpose

A ProofBundle is a deterministic, self-contained cryptographic artifact
designed to make an autonomous AI action independently verifiable,
auditable, and non-repudiable.

A ProofBundle MUST be verifiable without access to Immuva infrastructure.

---

## 2. Canonical Structure

A ProofBundle MUST be either:
- a directory, or
- a deterministic ZIP archive

It MUST contain the following files:

/proofbundle
├── events.jsonl
├── hashes.json
├── signature.json
├── manifest.json (OPTIONAL)
├── redaction_report.json (OPTIONAL)


No additional files are allowed unless explicitly ignored by the hashing
algorithm.

---

## 3. Deterministic Ordering

When zipped:
- Files MUST be ordered lexicographically
- No timestamps, compression randomness, or metadata MAY affect hashing
- ZIP output MUST be byte-identical for identical content

---

## 4. events.jsonl

- Append-only log of events
- Each entry MUST include:
  - event_id
  - event_type
  - timestamp
  - previous_event_hash
  - payload

Any modification invalidates the chain.

---

## 5. hashes.json

Contains:
- file path
- file size
- sha256 hash

All files except signature.json MUST be hashed.

---

## 6. Root Hash

The root hash MUST be computed as:

SHA256(concat(sorted(file_hashes)))

yaml
Copier le code

This root hash is the sole input to the signature process.

---

## 7. signature.json

The signature file MUST contain:

```json
{
  "algo": "ed25519",
  "root_hash": "...",
  "signature_hex": "...",
  "public_key_hex": "...",
  "proof_level": ["VALID", "..."],
  "created_at": "ISO-8601",
  "certificate": { ... } // OPTIONAL
}
8. Proof Levels
Proof levels communicate assurance strength:

VALID

KEY_PROTECTED

TIME_ANCHORED

CERTIFIED_IMMUVA

Levels are cumulative.

9. Verification Rules
A verifier MUST:

Recompute all file hashes

Recompute root hash

Verify signature

Verify event chain

Validate certificate and revocation (if present)

Failure at any step invalidates the proof.

10. Security Model
A ProofBundle provides:

Integrity

Identity binding

Temporal anchoring

Non-repudiation

It does NOT assert correctness of decisions.
