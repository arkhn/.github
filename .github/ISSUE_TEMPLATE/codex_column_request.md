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

- [ ] **Yes**: no Codex change, stop here. In the hospital repo, create `dbt/models/pivot/extended/pvt_<domain>_extended.sql`: it selects every column of the Codex `pvt_<domain>` and adds the transformed one. Local project models read `pvt_<domain>_extended` instead of `pvt_<domain>`.
- [ ] **No**: go on.

<!--
Example: month of birth, computed from birth_datetime.

-- dbt/models/pivot/extended/pvt_patient_extended.sql
select
    *,
    toMonth(birth_datetime) as month_of_birth
from {{ ref('pvt_patient') }}
-->



## 2. Is the column relevant for every source?

<!-- A request from one hospital is usually enough to show the column is relevant. -->

- [ ] **Yes**: add the column to the Codex pivot contract. Every source-pivot emits it as `null::Nullable(T)`, the requesting source fills it.
- [ ] **No**: the data is specific to this source. Map it to `pvt_observation`, or keep it in the hospital repo under `dbt/models/pivot/extended/`.


## 3. Raw column

<!-- Whatever the answer above, the column has to be available in raw. -->

- [ ] The column is added to the Codex raw model of the source.
- [ ] The pivot is updated: Codex `models/pivot/` (case **Yes** above) or hospital `dbt/models/pivot/extended/` (case **No**).


## Acceptance tests

<!-- Explain your expectations. -->


## Technical leads

<!-- Suggest ways to resolve this issue. -->
