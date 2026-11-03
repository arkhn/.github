---
name: Codex domain deployment
about: Add a domain from a source software to the Codex and deploy it in a hospital
title: '[<Source>] add <domain> domain'
type: "Task"
---

## User story statement & Context

<!-- Quel domaine, depuis quel logiciel, pour quel(s) client(s), et pour quel usage (projection, étude...). Lier les issues prérequises (domaines dont celui-ci dépend) et les mappings existants s'il y en a. -->

Ajouter ... de <Source> au Codex
Clients concernés : ...


## Acceptance tests (Mandatory)

Codex :
- [ ] Ajouter `<source>_pvt_<domain>` au Codex, avec tests unitaires et fixtures
- [ ] Colonnes PII taguées (`pii`, `not_salted`, `gen_and_loc`)

Déploiement à <hôpital> :
- [ ] Montée de version du Codex et ajout de la source dans `pivot_source_<domain>` (l'ordre décide de la déduplication)
- [ ] Run dev puis prod OK (codex + dagster), tests verts
- [ ] Volumétrie cohérente entre raw, staging et pivot, sans perte de lignes pour les autres sources du domaine
- [ ] Données validées sur un échantillon (avec l'hôpital si besoin)


## Technical leads (Optional)

<!-- Suggests ways to resolve this issue -->
