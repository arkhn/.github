# Description 
<!-- Describe the particularity of this env if necessary -->

# Test acceptance
<!-- Mandatory -->

Infra team:
- [] The "How to connect" page is created
- [] Presence of necessary passwords in bitwarden:
    - argocd
    - keycloak
    - code-server
    - clickhouse datalake
    - cloudbeaver
    - vault token
    - minio

- [] Check if at least 2 people can work at the same time
- [] Verify we can connect to the main web components from the Bastion or the dev workstation:
    - admin
    - dagit
    - cloudbeaver
    - keycloak (admin)
- [] Verify the metrics are pushed in AZmonitoring
- [] Verify the TLS is configured (no auto-signed certificate)
- [] Create the repository dagster-code-besancon on github
- [] Create arkhn-platform-dagster-user-deployments-k8s-dagster-code on argocd


Data team:
- [] Connection to the platform has been tested
- [] Test connection to various tools (at least keykloack, cloudbeaver, code-server)
- In code-server, test:
    - [] git clone
    - [] dbt debug
    - [] dbt deps

