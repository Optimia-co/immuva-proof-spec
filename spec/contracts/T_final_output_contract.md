# T-final — Output Contract (NORMATIVE)

Ce document définit le contrat de sortie JSON d'Immuva Proof v1.

## 1) Objet Verdict

### Champs autorisés (v1)
- mode?: "offline"
- status: "VALID" | "INVALID" | "PENDING" | "AWAITING_EVIDENCE" | "NON_CLOSABLE" | "CONTESTED"
- evidence?: Evidence
- outcome?: Outcome
- pointers?: Pointers
- violations?: ViolationCode[]
- errors?: string[] (non normatif : debug, ne doit pas être utilisé pour la décision)

### Ordre NORMATIF de sérialisation (comparaison texte)
1. mode
2. status
3. evidence
4. outcome
5. pointers
6. violations
7. errors

> Toute implémentation qui sérialise un Verdict DOIT respecter cet ordre si elle vise la conformance "text-compare".

## 2) Règles de présence
- mode est présent uniquement si offline=true
- evidence/outcome ne sont présents que si status le permet (ex: VALID -> evidence+outcome attendus)
- violations est présent uniquement si status in {"INVALID","CONTESTED","NON_CLOSABLE"} selon mapping

## 3) Forward compatibility
- Les champs inconnus DOIVENT être ignorés par les verifiers v1.
- Aucun champ existant ne doit changer de sémantique en v1.x.
