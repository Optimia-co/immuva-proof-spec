# P — Non-équivocation

Le protocole Immuva impose une règle stricte de non-équivocation.

Pour une même action et une même identité logique,
il ne peut exister qu’un seul événement canonique valide.

Si plusieurs événements canoniques distincts sont observés,
le verdict est INVALID sans possibilité de dégradation.

Cette violation est critique et ne dépend d’aucun mécanisme externe
(log de transparence, horodatage ou réseau).

La non-équivocation est évaluée localement par le verifier.

## P.X — Codes de violation

Le verifier v1 mappe les violations à des codes stables (registry-driven) :

- NON_EQUIVOCATION_VIOLATION : plus d’un encodage canonique distinct détecté dans le même périmètre d’identité d’événement.
