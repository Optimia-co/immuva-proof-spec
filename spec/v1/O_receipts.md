# O — Receipts

Les receipts sont des attestations associées à une action ou à un événement.
Elles modulent la capacité du verifier à conclure, sans jamais créer de faits.

## O.1 — Kinds autorisés

Les kinds de receipts autorisés en v1 sont :
- R1
- R2
- ENV_ATTEST
- NON_CLOSABLE

Tout receipt dont le kind n’appartient pas à cette liste entraîne un verdict INVALID.

## O.2 — Ordre et contraintes

- Les receipts sont évalués dans l’ordre fourni.
- Un receipt NON_CLOSABLE, s’il est présent, DOIT être terminal.
- Toute receipt apparaissant après NON_CLOSABLE entraîne un verdict INVALID.

## O.3 — Rôle de NON_CLOSABLE

NON_CLOSABLE indique que l’action ne pourra pas être clôturée proprement
(compte tenu des informations disponibles).

Effets normatifs :
- NON_CLOSABLE n’est PAS une preuve.
- NON_CLOSABLE n’autorise jamais VALID.
- NON_CLOSABLE permet une dégradation contrôlée vers NON_CLOSABLE
  au lieu de AWAITING_EVIDENCE lorsque l’évidence est insuffisante.

## O.4 — ENV_ATTEST (restriction stricte)

ENV_ATTEST est une attestation d’environnement.

Règle normative :
- ENV_ATTEST ne peut JAMAIS être utilisé comme basis d’un outcome.

Toute tentative d’utiliser ENV_ATTEST comme outcome.basis entraîne INVALID.

## O.5 — Dégradation et receipts

Les receipts ne modifient jamais les seuils de preuve requis.
Ils influencent uniquement la dégradation du verdict lorsque la preuve est
insuffisante ou non qualifiée.

Aucun receipt ne peut transformer une preuve insuffisante en VALID.

## O.X — Codes de violation

- RECEIPT_KIND_NOT_ALLOWED
- RECEIPT_LATE_AFTER_NON_CLOSABLE
- OUTCOME_BASIS_NOT_ALLOWED
- NON_CLOSABLE_SIGNAL
