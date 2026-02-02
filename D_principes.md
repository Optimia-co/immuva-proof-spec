# D — Principes de conception

## Déterminisme
À StubInput identique, le verifier produit toujours le même verdict.

## Ordre normatif strict
Les règles sont évaluées dans un ordre déterministe et immuable.
La première violation rencontrée fixe le verdict.

## Dégradation explicite
L’absence d’information ne conduit pas systématiquement à INVALID.
Le protocole distingue explicitement :
- PENDING
- AWAITING_EVIDENCE
- NON_CLOSABLE

## Offline-first
Le verifier n’effectue aucun accès réseau.
Toute vérification externe est hors scope v1.

## Aucune inférence
Le verifier ne déduit jamais de faits non présents dans l’input.
