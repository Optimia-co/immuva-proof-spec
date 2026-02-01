# Golden outputs — DEBUG/REFERENCE ONLY

Le dossier `golden/` sert uniquement au **debug** et à la comparaison avec une implémentation de référence.

La vérité normative de V est dans `vectors/**/expected/`.
Les tests de conformité **DOIVENT** comparer `output` vs `expected`, jamais vs `golden`.
