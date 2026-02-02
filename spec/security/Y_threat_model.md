# Y — Threat Model (NORMATIVE)

Ce document décrit les menaces couvertes par Immuva Proof v1.

## Principe
Chaque menace est liée à :
- un invariant
- un mécanisme
- un verdict observable

## Menaces couvertes (v1)

### Replay
- Menace : réutilisation d’un événement signé
- Invariant : encodage canonique unique
- Mécanisme : hash + non-équivocation
- Verdict : INVALID

### Équivocation
- Menace : plusieurs versions d’un même événement
- Invariant : unicité par scope
- Mécanisme : canonical JSON + set
- Verdict : INVALID

### Partial disclosure
- Menace : omission volontaire d’éléments
- Invariant : le verifier ne suppose rien
- Mécanisme : ResultSet gate
- Verdict : PENDING / AWAITING_EVIDENCE

### Forged receipt
- Menace : receipt inventé
- Invariant : allowlist + signature
- Mécanisme : registries
- Verdict : INVALID

### Out-of-order events
- Menace : modification de l’ordre
- Invariant : ordre fourni normatif
- Mécanisme : FSM / terminalité
- Verdict : INVALID

## Hors périmètre v1
Toute menace non listée ici est hors scope explicite.
