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

- [ ] **Yes**: the Codex pivot is not changed. In the hospital repo, create `dbt/models/pivot/extended/pvt_<domain>_extended.sql`: it selects every column of the Codex `pvt_<domain>` and adds the transformed one. Local project models read `pvt_<domain>_extended` instead of `pvt_<domain>`.

  Example: month of death, computed from `death_datetime`.

  ```sql
  -- dbt/models/pivot/extended/pvt_death_extended.sql
  select
      {{ dbt_utils.star(from=ref('pvt_death'), quote_identifiers=False) }},
      toMonth(death_datetime) as month_of_death
  from {{ ref('pvt_death') }}
  ```

- [ ] **No**: go on.


## 2. Is the column relevant for every source?

Most of the time, **yes: a request from one hospital is usually enough to show the column is relevant**. It still depends on the domain: if the data is only recorded by one software, it belongs in `pvt_observation`.

- [ ] **Yes**: add the column to the `pvt_<domain>` contract in Codex. The pivot unions every source-pivot by column position, so every source-pivot must output the new column: the requesting source fills it, all the others output an empty value of the same type.

  Example: social security number in `pvt_patient`, requested for one source.

  ```yaml
  # models/pivot/administrative/pvt_patient.yml
        - name: social_security_number
          data_type: Nullable(String)
  ```

  ```sql
  -- models/source/<requesting_software>/pivot/administrative/<requesting_software>_pvt_patient.sql
      ...
      social_security_number::Nullable(String) as social_security_number,

  -- every other <software>_pvt_patient.sql
      ...
      null::Nullable(String) as social_security_number,
  ```

- [ ] **No**: map the data to `pvt_observation` in the Codex source-pivot of the requesting source, one row per value. Mediboard already maps its vital signs this way.

  Example: a smoking status only recorded in the patient form of one software.

  ```sql
  -- models/source/<software>/pivot/clinical/<software>_pvt_observation.sql
  select
      ...
      'smoking_status' as observation_source_value,
      smoking_status as value_as_string,  -- e.g. 'former smoker'
      ...
  from {{ ref('<software>_stg_patient') }}
  ```


## 3. Need for a new raw column

Whatever the answers to the questions above, the column is added on the Codex side.

- [ ] The column is added to the Codex raw model of the source.
- [ ] The column is added to the Codex staging model of the source.


## Acceptance tests

<!-- Explain your expectations. -->


## Technical leads

<!-- Suggest ways to resolve this issue. -->
