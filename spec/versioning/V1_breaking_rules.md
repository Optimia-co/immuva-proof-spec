# V1 — Breaking vs Non-Breaking Rules (NORMATIVE)

Ce document définit ce qui invalide une preuve Immuva Proof v1.

## Principe fondamental
Une preuve v1 est valide **uniquement** si elle est vérifiée contre :
- la spec v1
- les registries v1 exactes (hash inclus)
- un verifier conforme v1

## BREAKING (preuve INVALID ou non vérifiable)

Une preuve est considérée **cassée** si :

- le canonical encoding change
- l’ordre normatif des champs change
- un champ obligatoire est retiré
- un invariant de sécurité est modifié
- un violation_code change de sémantique
- un registry change sans bump de version
- une règle BREAK devient DEGRADE
- une signature v1 n’est plus valide

➡️ Toute modification BREAKING nécessite **v2**.

## NON-BREAKING (preuve toujours valide)

Ne cassent PAS une preuve v1 :

- ajout de champs optionnels ignorables
- ajout de nouveaux violation_codes
- ajout de nouveaux kinds non utilisés
- ajout de nouveaux registries versionnés
- amélioration documentaire sans impact normatif

➡️ Ces changements sont autorisés en **v1.x**.

