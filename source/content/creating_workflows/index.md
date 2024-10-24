# Creating CI/CD Scripts

YAML is extensively used in defining workflows and pipelines in both GitHub and GitLab:

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./yaml_primer/index
./variable_syntax
./advanced_variable_syntax
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./yaml_primer/index.md
```
```{include} ./variable_syntax.md
```
```{include} ./advanced_variable_syntax.md
```
```{include} ./github/index.md
```
```{include} ./gitlab/index.md
```
{% endif %}
