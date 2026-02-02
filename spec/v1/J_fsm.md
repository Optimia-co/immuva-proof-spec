# J — Machine à états finie (FSM)

La FSM Immuva définit l’ordre normatif des événements associés à une action.

Elle garantit :
- l’unicité de clôture,
- l’absence d’ambiguïté temporelle,
- la cohérence structurelle des preuves.

## J.1 — États normatifs

Les états suivants sont définis :

- INIT        : état initial implicite
- OPEN        : action en cours
- FINISHED    : action clôturée
- INVALID     : état terminal d’erreur structurelle

INIT et OPEN sont des états transitoires.
FINISHED et INVALID sont terminaux.

## J.2 — Transitions autorisées

Transitions valides :

- INIT  → OPEN
- OPEN  → OPEN        (événements intermédiaires)
- OPEN  → FINISHED

Toute autre transition est interdite et entraîne INVALID.

## J.3 — Unicité de clôture

Une action ne peut être clôturée qu’une seule fois.

Toute tentative de :
- double FINISHED,
- FINISHED suivi d’un événement,

entraîne une violation FSM et un verdict INVALID.

## J.4 — Action ID unique

Tous les événements associés à une action
DOIVENT partager le même action_id.

Si plusieurs action_id distincts sont observés
dans une même preuve, le verdict est INVALID.

## J.5 — Effet sur le verdict

Les violations FSM sont critiques :

- elles ne peuvent pas être dégradées,
- elles entraînent INVALID immédiatement,
- elles sont indépendantes de l’évidence ou des receipts.
