---
name: QA Deployment
about: List of verification steps on a new environment
---

# Description 
<!-- Describe the particularity of this env if necessary -->

# Acceptance tests
<!-- Mandatory -->

Infra team:
- [ ] The "How to connect" page is created
- [ ] Presence of necessary passwords in bitwarden:
    - argocd
    - keycloak
    - code-server
    - clickhouse datalake
    - cloudbeaver
    - vault token
    - minio

- [ ] Check if at least 2 people can work at the same time
- [ ] Verify we can connect to the main web components from the Bastion or the dev workstation:
    - admin
    - dagit
    - cloudbeaver
    - keycloak (admin)
- [ ] Verify the metrics are pushed in AZmonitoring
- [ ] Verify the TLS is configured (no auto-signed certificate)
- [ ] Create the corresponding repository dagster-code- on dockerhub

Documentation (Infra team)
- [ ] _matrice de flux_ is up to date has been shared with the client and can be found in Arkhn drive or Notion for this project
- [ ] [recapitulatif de nos environnements](https://docs.google.com/spreadsheets/d/1F_vPzAkQai56mJirW4nuIr4HnAOnrGgGtypJUDHQiHs/edit?gid=0#gid=0) has been updated
- [ ] in "récapitulatif de nos environnements", the tab "procédure de sauvegardes" has been filled with the backup procedure for this project. If the is no backup procedure for this env, a ticket is open for this. 

Data team:
- [ ] Connection to the platform has been tested
- [ ] Test connection to various tools (at least keykloack, cloudbeaver, code-server)
- In code-server, test:
    - [ ] git clone
    - [ ] dbt debug
    - [ ] dbt deps
