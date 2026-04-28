---
name: Environment initialization procedure
about: List of action for setting a new environment
---

## Description of the environment


<!-- Describe the environment in few words -->
<!-- link the "fiche navette" -->


<!-- Precise which components/apps must be deployed -->
Components enabled:

- [ ] DCR + Local Nexus
- [ ] GPU for DCR
- [ ] GPU for Dagster
- [ ] Explore
- [ ] Superset
- [ ] Clickhouse
- [ ] Dagster
- [ ] Coder
- [ ] MatchID
- [ ] Nerd
- [ ] Datahub

## Preflight checklist

- [ ] run the [preflight script](https://github.com/arkhn/cli/tree/main) on all machines
- [ ] Save the script output in the comments of the current issue

## Documentation

- [ ] create and update the [Infra Checklist](https://docs.google.com/spreadsheets/d/1Gxq5VccU9CyndQLhILy2upkEj58E3iC8qxXZIowHT4E/edit?gid=0#gid=0)
- [ ] create the network matrix from the [template](https://docs.google.com/spreadsheets/d/1DmaULtgDDKnj5_9cpxtTMeu2dCMGq7lOGWmJu67blDI/edit?gid=0#gid=0)
- [ ] record the new environment in the [env summary](https://docs.google.com/spreadsheets/d/1F_vPzAkQai56mJirW4nuIr4HnAOnrGgGtypJUDHQiHs/edit?gid=0#gid=0)
- [ ] create the ["How to connect" page](https://www.notion.so/arkhn/Hospital-access-How-to-connect-to-cde891dea219407f90182dd1a7373c90?source=copy_link)

## Deployment

- [ ] Set the SSH public key in the target machines
- [ ] Change `REPLACE_ME` placeholders in the `deployment-*` repo
- [ ] Configure the `arkhn-platform` app
- [ ] [Install Arkhn CLI](https://www.notion.so/arkhn/Installation-procedure-ea3aa3e34c7845bea611a80445c77b85?source=copy_link)
- [ ] Deploy Neogeo
- [ ] Deploy ArgoCD Apps
- [ ] Record passwords in bitwarden:
    - argocd
    - keycloak
    - clickhouse datalake
    - coder
    - vault token
    - minio
- [ ] Configure the metrics remote writing toward AZmonitoring
- [ ] Configure TLS
- [ ] Configure [SSO](https://www.notion.so/arkhn/Connexion-OIDC-avec-un-tablissement-2b6403a7adf38067a27fc5a528f3364e?source=copy_link) (OIDC or SAML ) or LDAP
- [ ] Configure [SFTP](https://www.notion.so/arkhn/Serveur-SFTP-2f5403a7adf380448cc4d2026c543ce3?source=copy_link)
- [ ] Configure backups (don't forget the related tab in the environnement inventory)
- [ ] Create the corresponding repository dagster-code- on dockerhub

## QA Checklist

- [ ] Run the compliance script and save the output in the comments of the current issue
- [ ] Verify that data storages (Clickhouse, MinIO, Logs) are in line with client's requirements
- [ ] Check if at least 2 people can work at the same time
- [ ] Verify we can connect to the main web components from the Bastion or the dev workstation:
    - Arkhn admin
    - dagit
    - coder (workspace creation test)
    - keycloak (admin)
    - grafana
    - DCR (test connection to local admin)
- [ ] Verify the metrics are pushed in AZmonitoring
- [ ] Verify we can download packages from the DCR (internal nexus enabled)
- [ ] Verify the TLS is configured (no auto-signed certificate)
- [ ] Specify the method to use to create a workspace in coder (SSH key or token) in the README and the how to connect page
- [ ] Specify if keycloak is synchronized with the hospital's Active Directory (LDAP/AD) or connected to the hospital's SSO
