# U — Vérification hors ligne

En mode offline :
- aucun appel réseau n’est effectué,
- aucun Transparency Log n’est requis,
- le verdict est produit uniquement à partir de StubInput.

Le mode offline ajoute le champ "mode": "offline" au verdict,
sans modifier la logique de calcul du statut.
