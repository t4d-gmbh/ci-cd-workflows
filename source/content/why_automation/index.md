# Why 🤖 Automation?

## What is CI/CD?
:::{card} Continuous Integration (CI)
* Automate testing, building, and validation of code changes.
:::
:::{card} Continuous Deployment (CD)
* Automate deployment of validated code changes to production.
:::

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./benefits
./for_non_sd
./how_automation_helps
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./benefits.md
```
```{include} ./for_non_sd.md
```
```{include} ./how_automation_helps.md
```
{% endif %}
