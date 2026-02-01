# Conformance profiles (v1)

Un **profile** définit un **ensemble de vectors normatifs** (un “set” de tests V) associé à une `spec_version`.

Règles :
- Un profile est **normatif** : il dit quels vectors font partie de la conformité.
- Un profile est **append-only** dans une même ligne compatible.
- Toute modification non-append-only implique une **nouvelle version** (SemVer) et une `spec_version` explicite.
