# V — Mapping ViolationCode -> VerdictStatus (NORMATIVE)

Ce document fixe le mapping v1 entre violations et statuts.

## Principes
- INVALID : violation de structure, de signature, d'ordre, ou d'invariant core.
- CONTESTED : conflit de basis, contradictions admissibles (preuve contestable).
- NON_CLOSABLE : présence explicite d'un signal NON_CLOSABLE + condition empêchant VALID.

## Règles
- Une violation avec default_status=INVALID implique status=INVALID.
- Si aucune INVALID mais au moins une CONTESTED => status=CONTESTED.
- Si aucune INVALID/CONTESTED mais NON_CLOSABLE => status=NON_CLOSABLE.
- PENDING / AWAITING_EVIDENCE ne transportent pas de violations (v1).

> Les vectors définissent les verdicts attendus. Ce mapping doit rester cohérent avec les expected JSON.
