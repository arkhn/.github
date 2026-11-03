---
name: Codex domain deployment
about: Deploy a Codex domain (pvt_<domain>) from a source software in one hospital
title: '[<hospital>] Deploy <domain> from <source>'
type: "Task"
---

## Description
<!-- Which domain, from which source software, in which hospital, and why (projection, study, client request...). -->


| | |
|---|---|
| Hospital / environment | <!-- e.g. besancon --> |
| Domain | <!-- e.g. pvt_location --> |
| Source software(s) | <!-- e.g. resurgences --> |
| Codex version carrying the models | <!-- vX.X.X --> |
| Consuming projections | <!-- admin / explore / omop / omop_hdh / orchidee / none --> |

## Related links
- Codex PR(s): <!-- link -->
- Mapping issue(s): <!-- link -->
- deployment-hospital PR: <!-- link -->

## Prerequisites
<!-- Everything here must be true before touching the deployment. -->
- [ ] The `<source>_pvt_<domain>` models are merged in Codex **and released** in the version above
- [ ] The source tables are reachable from the hospital (JDBC connection, schema and table names checked against the `_<source>__<schema>__sources.yml`)
- [ ] The domains this one depends on are already deployed for this hospital (patient, visit_occurrence, care_site... — check the `relationships` tests of `<source>_pvt_<domain>.yml`)
- [ ] Every new PII column has an explicit tagging decision (`pii`, `not_salted`, `gen_and_loc`), see [7_contrib_encryption_data.md](https://github.com/arkhn/codex/blob/main/documentation/7_contrib_encryption_data.md)

## Steps in deployment-hospital
1. [ ] Bump Codex in `packages.yml` to the version above
2. [ ] Re-enable the source's models under `models: codex:` in `dbt_project.yml`, if they are disabled for this hospital
3. [ ] Add the source to `pivot_source_<domain>`. **The order decides which source wins on deduplication**: append it at the tail unless this hospital needs it first, and say why here
4. [ ] Set the hospital-specific variables, if any:
    - [ ] `filter_date_raw`
    - [ ] custom filters `<source>_filter_<domain>` + their `cst_filter_*` models (see [10_customize_models.md](https://github.com/arkhn/codex/blob/main/documentation/10_customize_models.md))
    - [ ] model overwrites (same doc)
5. [ ] Run on **dev**: `dbt build -s +<source>_pvt_<domain>+` (or the Dagster dev run) — all tests green
6. [ ] Deploy the Dagster code (see [8_contrib_deploy_dagster_code.md](https://github.com/arkhn/codex/blob/main/documentation/8_contrib_deploy_dagster_code.md))
7. [ ] Run on **prod**

## Post-deployment checks
- [ ] Row counts are consistent from raw to staging to `<source>_pvt_<domain>` to `pvt_<domain>`; every drop is explained by a documented filter
- [ ] `pvt_<domain>` holds the expected rows for `source_value = '<source>'`, and the other sources of the domain did not lose rows
- [ ] PII columns are encrypted in the datalake (spot-check a few rows)
- [ ] The consuming projections are rebuilt and show the new data
- [ ] Business validation: a sample of records checked against the source software, with the hospital if needed
<!-- Paste the counts / queries used here. -->


## Rollback plan
<!-- Default: remove the source from pivot_source_<domain>, revert packages.yml if it was bumped for this, rerun the domain and its projections. -->


## Definition of Done
- [ ] Domain running in prod, tests green
- [ ] Post-deployment checks done and their results pasted above
- [ ] Hospital / project team informed
