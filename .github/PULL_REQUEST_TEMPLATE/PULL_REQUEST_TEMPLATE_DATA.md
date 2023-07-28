<!---
Provide a short summary in the Title above. Examples of good PR titles:
* "Feature: add so-and-so models"
* "Fix: deduplicate such-and-such"
* "Update: dbt version 0.13.0"
-->

## Description & motivation
### Short description
<!---
Describe your changes, and why you're making them. Is this linked to an open
issue ? Link it here.
-->
### Issue and Author

Fixes #[issue number] by @[issue author]

### Screenshot
<!---
Include a screenshot of the relevant section of the updated DAG. You can access
your version of the DAG by running `dbt docs generate && dbt docs serve`.
-->

## Data Checklist
### Template - New model / Update model

- [ ] I have written tests on primary keys and it works
- [ ] I have written tests on foreign keys and it works
- [ ] I have written the related documentation
- [ ] I have formatted the model with SQLfmt
- [ ] I have checked if the model is SQLFLUFF compliant
- [ ] I have validated the model (dbt run works on my branch)
- [ ] I have run FHIR validate if needed


### Template - Fix model

- [ ] I have formatted the model with SQLfmt
- [ ] I have checked if model is SQLFLUFF compliant
- [ ] I have validated the model (dbt run works on my branch)
- [ ] I have validated the related tests (Primary key, Foreign key, etc.)
- [ ] I have run FHIR validate if needed
- [ ] I have shared this issue with my team (channel data-team)

### POST MERGE CHECKLIST

- [ ] I will remove old tables from the Datalake once I have modified (or deleted) a model name
- [ ] I will check if dbt run is still working on main
- [ ] I will check if dbt test is still working on main
