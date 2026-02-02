# X — BREAK vs DEGRADE (NORMATIVE)

Ce document définit la politique de sécurité v1 d’Immuva Proof.

## Principe fondamental
Une preuve Immuva Proof ne peut jamais produire un faux VALID.

Elle peut :
- BREAK : produire INVALID
- DEGRADE : refuser de conclure (PENDING / AWAITING_EVIDENCE / NON_CLOSABLE / CONTESTED)

## Règle absolue
Aucune dégradation ne peut produire un verdict VALID.

## Tableau normatif

| Situation | Effet | Verdict |
|----------|------|--------|
| Signature invalide | BREAK | INVALID |
| Key binding incorrect | BREAK | INVALID |
| Non-équivocation violée | BREAK | INVALID |
| Receipt interdit | BREAK | INVALID |
| Receipt après NON_CLOSABLE | BREAK | INVALID |
| ResultSet manquant | DEGRADE | PENDING |
| Evidence insuffisante | DEGRADE | AWAITING_EVIDENCE |
| NON_CLOSABLE explicite | DEGRADE | NON_CLOSABLE |
| Conflit admissible de basis | DEGRADE | CONTESTED |

## Source de vérité
Ce tableau doit rester cohérent avec :
- registries/v1/violation_codes.json
- les vectors de conformance
- le comportement réel du verifier
