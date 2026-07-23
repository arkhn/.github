---
name: "🛫 Pre-flight check"
about: Vérification technique d'un environnement client avant déploiement
title: "[<Client>] Pre-flight check"
labels: ["type/feature"]
assignees: []
---

## Context

Contact système (à contacter si problèmes de conf) : <Nom Prénom> <email>

## Platform specification

Pré-requis techniques

- Number of nodes: X
- Number of CPU per node: X
- RAM capacity per node: X
- Disk storage (data) per node: X

La matrice de flux a été partagée au client et nous a été renvoyée complétée en partie : lien ici

## Documentation

- [ ] create/update the [Infra Checklist]
- [ ] create/update the network matrix from the template
- [ ] record the new environment in the env summary

## Preflight checklist

- [ ] run the preflight script on all machines (`arkhn-cli preflight`)
- [ ] Save the script output in the comments of the current issue
