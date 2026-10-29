---
name: Update all environments
about: Deploy, migrate, upgrade, or bump a version across every environment
title: ''
type: "Task"
---

## Description
<!-- What has to be done (deployment, migration, upgrade, version bump, secret rotation...) and why. Link the related PR, release, or ticket. -->


## Type of change
<!-- Tick every type that applies. -->
- [ ] Data: Codex / dbt (version bump, migration, full refresh...)
- [ ] Data: Dagster (release, job or schedule change...)
- [ ] Platform: helm-charts / Kubernetes / Argo CD
- [ ] Application: admin, explore, nerd, text-extraction...
- [ ] Infrastructure: machines, network, storage, GPU...
- [ ] Security: secret or certificate rotation, access change...
- [ ] Other:

## Versions to deploy
<!-- Delete the lines that do not apply. -->
- codex: vX.X.X
- dagster: vX.X.X
- helm-charts: vX.X.X
- admin: vX.X.X

## Documentation
- [Release Notes](<link to the release notes>)
- [Procedure](<link to the procedure documentation>)

## Steps to apply
<!-- Commands, scripts, or manual steps to run in each environment. -->
1.
2.
3.

## Post-update checks
<!-- Tests to run in each environment once the change is applied. -->


## Rollback plan
<!-- How to revert if something goes wrong. -->


## Environments
<!-- Leave unchecked when creating the issue. Tick each one once the change is applied and verified there. -->
- [ ] azure
- [ ] demo
- [ ] besancon
- [ ] chuga
- [ ] clermont-edd
- [ ] fss-edd
- [ ] hcl
- [ ] icm
- [ ] iuct
- [ ] metz-thionville
- [ ] nice
- [ ] ramsay
- [ ] reunion
- [ ] telethon
- [ ] toulouse
- [ ] vivalto
