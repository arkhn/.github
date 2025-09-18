---
name: Environment initialization procedure
about: List of action for setting a new environment
---

## Description of the environment


<!-- Describe the environment in few words -->
<!-- link the "fiche navette" -->


<!-- Precise which components/apps must be deployed -->
Components enabled:

- [ ] DCR
- [ ] GPU
- [ ] Superset
- [ ] Clickhouse
- [ ] Dagster
- [ ] Coder


## Preflight checklist

- [ ] run the [compliance script](https://github.com/arkhn/helm-charts/tree/main/compliance) on all machines
- [ ] Record the script output in the comments of the current issue


## Documentation

- [ ] create the network matrix from the [template](https://docs.google.com/spreadsheets/d/1DmaULtgDDKnj5_9cpxtTMeu2dCMGq7lOGWmJu67blDI/edit?gid=0#gid=0)
- [ ] record the new environment in the [env summary](https://docs.google.com/spreadsheets/d/1F_vPzAkQai56mJirW4nuIr4HnAOnrGgGtypJUDHQiHs/edit?gid=0#gid=0)

## Deployment

- [ ] Set the SSH public key in the target machines
- [ ] Change `REPLACE_ME` placeholders in the `deployment-*` repo
- [ ] Configure the `arkhn-platform` app
- [ ] [Install Arkhn CLI](https://www.notion.so/arkhn/Installation-procedure-ea3aa3e34c7845bea611a80445c77b85?source=copy_link)
- [ ] Deploy Neogeo
- [ ] Deploy ArgoCD Apps

