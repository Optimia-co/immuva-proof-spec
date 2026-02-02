# F — Encodage canonique (Canonical Encoding)

L’encodage canonique définit une représentation unique et déterministe
d’un événement ou d’un artefact signé.

## F.1 — Objectif

- Éliminer toute ambiguïté de sérialisation.
- Garantir que deux implémentations produisent la même empreinte.
- Servir de base aux signatures et à la non-équivocation.

## F.2 — Format de base

En v1, l’encodage canonique est une chaîne UTF-8 représentant un JSON canonique.

Les règles suivantes sont normatives :

- Les objets JSON sont sérialisés avec :
  - des clés triées lexicographiquement (ordre Unicode).
  - aucune clé dupliquée.
- Les tableaux conservent l’ordre fourni.
- Aucun espace superflu (minified).
- Les chaînes sont encodées en UTF-8.
- Les nombres sont sérialisés sans notation scientifique.

## F.3 — Types autorisés

- null
- boolean
- number (entier ou décimal)
- string
- array
- object

Tout type non JSON (Date, BigInt, bytes, etc.) est interdit.

## F.4 — Champs ignorés

En v1, le verifier n’ignore aucun champ présent dans l’événement canonique.
Toute variation de contenu entraîne une variation de l’encodage canonique.

## F.5 — Lien avec les signatures (v1)

En v1, une signature valide est définie comme :

signature == hex(sha256(canonical_event))

Toute divergence d’encodage entraîne SIGNATURE_INVALID.

## F.6 — Non-équivocation

Deux événements sont considérés distincts si et seulement si
leur encodage canonique diffère octet par octet.
