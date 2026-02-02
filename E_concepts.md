# E — Concepts fondamentaux

## StubInput
Structure d’entrée agrégée fournie au verifier.

Champs principaux :
- resultset_present (bool)
- evidence (StubEvidence)
- outcome (StubOutcome)
- pointers (StubPointers)
- receipts (StubReceipt[])
- canonical_event / canonical_events
- signing / key_binding
- terminal_present (hint)

## Evidence
Définit un niveau effectif et requis de preuve :
- effective : "R1", "R2", …
- required : "R1", "R2", …
- qualified : bool

## Outcome
Résultat revendiqué par l’agent, associé à une base de preuve.

## Receipts
Attestations optionnelles participant aux règles de clôture.

## Statuts normatifs

- VALID
- INVALID
- PENDING
- AWAITING_EVIDENCE
- NON_CLOSABLE
- CONTESTED
