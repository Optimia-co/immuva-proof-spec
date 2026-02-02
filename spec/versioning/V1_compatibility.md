# V1 — Compatibility Rules (NORMATIVE)

Ce document définit la compatibilité descendante d’Immuva Proof v1.

## Règle d’or
Tout verifier v1.x DOIT pouvoir vérifier toute preuve v1 antérieure.

## Autorisé en v1.x
- Nouveaux violation_codes
- Nouveaux kinds / receipts
- Nouveaux champs optionnels
- Nouveaux profils de conformance

## Interdit en v1.x
- Modifier la signification d’un verdict
- Modifier le canonical encoding
- Modifier l’ordre normatif de sérialisation
- Supprimer un champ existant
- Changer une règle BREAK ↔ DEGRADE

## Migration
- Aucune migration automatique n’est autorisée en v1
- Toute rupture implique v2

