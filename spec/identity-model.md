# Immuva Identity Model

## Overview

Immuva is built on a zero-trust identity model.

Every autonomous agent acts under its own cryptographic identity.
Actions are signed by the agent itself — not by Immuva.

Immuva does not act as an executor or validator.
It acts as a cryptographic notary for identity binding.

---

## Identity vs Action

Immuva strictly separates:

- **Identity** — who is acting
- **Action** — what was done
- **Proof** — cryptographic evidence that the action occurred

An action without identity is not accountable.
An identity without proof is deniable.

Immuva binds both.

---

## Agent Key Generation

Each agent generates its own cryptographic key pair locally:

```bash
immuva keygen --org "Acme Corp" --env prod
Private keys never leave the agent environment

Key generation is deterministic and auditable

Multiple environments are supported (dev / staging / prod)

Immuva never generates or stores private keys.

Certification (Identity Binding)
To make an identity legally meaningful, the agent public key can be certified.

The certification process:

The agent generates a CSR (Certificate Signing Request)

The CSR is submitted to Immuva Authority

Immuva Authority verifies the legal entity

A certificate is issued binding:

public key

organization

environment

validity period

This creates a cryptographic link between an agent and a legal entity.

Self-Carrying Proofs
Each ProofBundle embeds:

the action

the signature

the certificate (if present)

This makes proofs self-verifiable and portable.

No online lookup is required.
No dependency on Immuva infrastructure is required.

Revocation
If an agent key is compromised, it can be revoked immediately.

Immuva maintains a signed Certificate Revocation List (CRL).

During verification:

revoked keys fail verification

past proofs remain valid but flagged

This aligns with standard PKI security practices.

Trust Model Summary
Immuva does not require trust in its servers.

Trust is derived from:

cryptographic signatures

deterministic verification

transparent revocation

Immuva provides proof.
Responsibility remains with the agent owner.
