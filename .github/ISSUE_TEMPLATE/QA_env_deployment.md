---
name: QA Deployment
about: List of verification steps on a new environment
---

# Description 
<!-- Describe the particularity of this env if necessary -->

# Acceptance tests


Data team:
- Coder workspace:
    - code-server:
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
