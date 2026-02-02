# A — Finalité normative

Immuva Proof v1 définit un protocole de vérification déterministe produisant
un verdict normatif à partir d’un input agrégé (StubInput).

Le protocole évalue uniquement la cohérence interne entre :
- un résultat revendiqué (Outcome),
- un niveau de preuve déclaré (Evidence),
- des reçus optionnels (Receipts),
- des invariants cryptographiques minimaux.

Immuva Proof ne prétend pas :
- établir la vérité du monde réel,
- inférer des faits absents de l’input,
- interpréter l’intention de l’agent.

Le protocole est :
- verifier-first (le comportement du verifier fait foi),
- offline-first,
- déterministe,
- asynchrone par conception.
