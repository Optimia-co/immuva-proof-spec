# G — Modèle d’événement (Event Model)

Un événement Immuva est une structure atomique décrivant un fait associé
à une action. Les événements sont évalués séquentiellement par le verifier
et soumis aux règles FSM.

## G.1 — Schéma minimal

Un événement DOIT contenir les champs suivants :

- kind (string)
- action_id (string)
- event_id (string)

Les champs suivants sont optionnels en v1 :
- payload (object)
- timestamp (string, opaque)
- metadata (object)

Aucun autre champ n’est interprété par le verifier v1.

## G.2 — Contraintes normatives

- kind DOIT correspondre à un kind enregistré dans `kinds.json`.
- action_id DOIT être identique pour tous les événements d’une même action.
- event_id DOIT être unique dans le périmètre de l’action.
- Les événements sont évalués dans l’ordre fourni.

## G.3 — Terminalité

La terminalité d’un événement est déterminée par son kind :

- Les kinds marqués `terminal=true` dans `kinds.json` clôturent l’action.
- Aucun événement ne peut suivre un événement terminal.
- Toute violation entraîne INVALID (violation FSM).

## G.4 — Neutralité sémantique

Le verifier n’infère jamais :
- ni l’intention,
- ni la causalité,
- ni la vérité du payload.

Le modèle d’événement est strictement structurel.
