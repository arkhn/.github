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
- Coder workspace:
    - code-server: <specify the method: ssh or token>
        - [ ] clone the 3 repositories (codex, dagster, deployment-hospital)
        - [ ] venv and .env are automatically created
        - [ ] deployment-hospital is up to date (with the latest versions of deployment-template, dagster and codex)
        - [ ] dbt debug runs successfully
        - [ ] dbt deps runs successfully
        - [ ] dbt build runs successfully (activate OMOP models, which also checks for the presence of omop_extended tables)

    - cloudbeaver: 
        - [ ] the connection to the datalake is automatically added
        - [ ] the connection is working
        - [ ] the tables are present in the datalake after the "run_all" on prod and dev (cf Dagster/Dagit point )
        
- ArgoCD:
    - [ ] connection is working
    - [ ] deployment of dagster-code and dagster-code-dev is successful

- Dagster/Dagit:
    - [ ] connection is working
    - [ ] run "run all" on both prod and dev on Dagit

- Arkhn interface:
    - [ ] dbt docs is accessible
    - [ ] dataset previsualisation is working
