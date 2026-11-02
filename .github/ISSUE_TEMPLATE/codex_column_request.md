---
name: Codex column request
about: A hospital needs a piece of data the Codex pivot does not expose yet
title: ''
labels: "type/mapping"
---

## Need (Mandatory)

<!-- Which hospital, which data, for which use (project, OMOP, Explore...). -->

- Hospital:
- Data needed:
- Use:
- Source software and table/column:


## 1. Is the data already in the pivot? (Mandatory)

<!-- Look for the data, or something it can be computed from, in the existing pvt_* models. -->

- [ ] **Yes**: it is a transformation of existing pivot columns. Do it in the hospital repo, under `dbt/models/pivot/extended/`. No Codex change, stop here.
- [ ] **No**: go on.


## 2. Is the column relevant for every source? (Mandatory)

<!-- A request from one hospital is usually enough to show the column is relevant. -->

- [ ] **Yes**: add the column to the Codex pivot contract. Every source-pivot emits it as `null::Nullable(T)`, the requesting source fills it.
- [ ] **No**: the data is specific to this source. Map it to `pvt_observation`, or keep it in the hospital repo under `dbt/models/pivot/extended/`.


## 3. Raw column (Mandatory)

<!-- Whatever the answer above, the column has to be available in raw. -->

- [ ] The column is added to the Codex raw model of the source.
- [ ] The pivot is updated: Codex `models/pivot/` (case **Yes** above) or hospital `dbt/models/pivot/extended/` (case **No**).


## Acceptance tests (Mandatory)

<!-- Explain your expectations. -->


## Technical leads (Optional)

<!-- Suggest ways to resolve this issue. -->
