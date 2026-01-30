# Immuva Proof Levels

## Overview

Not all proofs provide the same level of assurance.

Immuva defines explicit proof levels to match different
security, audit, and regulatory requirements.

Each level is additive and verifiable.

---

## Proof Levels

### VALID

**Guarantees**
- File integrity
- Deterministic hashing
- Immutable event chain

**What it proves**
- The action occurred
- The data was not modified

**Typical usage**
- Internal audit logs
- Debugging
- Non-regulated systems

---

### KEY_PROTECTED

**Guarantees**
- Action signed with a protected private key
- Key stored in HSM, enclave, or secure signer

**What it proves**
- The signer controlled the key securely
- The action was not forged

**Typical usage**
- Security audits
- Enterprise-grade systems
- SOC2 / ISO27001 environments

---

### TIME_ANCHORED

**Guarantees**
- Independent cryptographic timestamp
- Proof of existence at a given time

**What it proves**
- The action existed at or before a specific moment
- The proof is resistant to backdating

**Typical usage**
- Legal precedence
- Dispute resolution
- Regulatory reporting

---

### CERTIFIED_IMMUVA

**Guarantees**
- Signing key bound to a verified legal entity
- Identity certified by Immuva Authority
- Revocation-aware verification

**What it proves**
- Who is legally responsible
- Under which organization and environment
- That the identity was valid at signing time

**Typical usage**
- AI Act compliance
- Financial systems
- Contracts and liability attribution

---

## Verification Semantics

Verification is deterministic.

A proof is either:
- valid
- invalid
- revoked

There is no partial trust or heuristic scoring.

---

## Design Rationale

Proof levels allow:

- progressive adoption
- explicit risk modeling
- regulator-friendly guarantees

Immuva does not decide which level to use.
The system designer does.

Immuva enforces verifiability.

