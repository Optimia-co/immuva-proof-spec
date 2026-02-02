# Z — Offline-first Security Model (NORMATIVE)

Ce document décrit le modèle de sécurité offline d’Immuva Proof.

## Ce que l’offline protège
- Audit différé
- Vérification long terme
- Absence de tiers de confiance
- Résilience à la censure réseau

## Ce que l’offline ne protège pas
- Disponibilité temps réel
- Synchronisation globale
- Prévention d’actions futures

## Principe fondamental
Immuva Proof ne protège pas l’action.
Il protège la preuve de l’action.

## Conséquence
Un verdict offline peut être :
- VALID
- INVALID
- PENDING
- NON_CLOSABLE

Mais il est toujours vérifiable sans dépendance réseau.
