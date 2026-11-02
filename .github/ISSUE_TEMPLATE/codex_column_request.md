---
name: Codex column request
about: A hospital needs a piece of data the Codex pivot does not expose yet
title: ''
labels: "type/mapping"
---

## Need

<!-- Which hospital, which data, for which use (project, OMOP, Explore...). -->

- Hospital:
- Data needed:
- Use:
- Source software and table/column:


## 1. Can the data be obtained by a transformation of existing pivot data?

<!-- Look in the existing pvt_* models for columns the data can be computed from. -->

If yes, no Codex change: in the hospital repo, create `dbt/models/pivot/extended/pvt_<domain>_extended.sql`. It selects every column of the Codex `pvt_<domain>` and adds the transformed one. Local project models read `pvt_<domain>_extended` instead of `pvt_<domain>`.

Example: month of death, computed from `death_datetime`.

```sql
-- dbt/models/pivot/extended/pvt_death_extended.sql
select
    {{ dbt_utils.star(from=ref('pvt_death'), quote_identifiers=False) }},
    toMonth(death_datetime) as month_of_death
from {{ ref('pvt_death') }}
```

- [ ] **Yes**: create the extended model above, stop here.
- [ ] **No**: go on.


## 2. Is the column relevant for every source?

Most of the time, yes: a request from one hospital is usually enough to show the column is relevant. It still depends on the domain: data that only one software records belongs in `pvt_observation`.

Example: a smoking status only recorded in the patient form of one software becomes one `pvt_observation` row per patient, with `observation_source_value = 'smoking_status'` and `value_as_string = 'former smoker'`. Mediboard already maps its vital signs this way, one row per variable.

- [ ] **Yes**: add the column to the Codex pivot contract. Every source-pivot emits it as `null::Nullable(T)`, the requesting source fills it.
- [ ] **No**: map the data to `pvt_observation` in the Codex source-pivot of the requesting source.


## 3. Need for a new raw column

Whatever the answer to question 2, the column is added on the Codex side.

- [ ] The column is added to the Codex raw model of the source.
- [ ] The column is added to the Codex staging model of the source.
- [ ] The pivot is updated: `pvt_<domain>` contract (question 2 **Yes**) or `pvt_observation` (question 2 **No**).


## Acceptance tests

<!-- Explain your expectations. -->


## Technical leads

<!-- Suggest ways to resolve this issue. -->
