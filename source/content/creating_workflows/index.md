# Creating CI/CD Workflows

YAML is extensively used in defining workflows and pipelines in both GitHub and GitLab:

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./variable_syntax
./github_workflow
./github_workflow_structure
./gitlab_workflow
./gitlab_pipeline_structure
./advanced_variable_syntax
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./variable_syntax.md
```
```{include} ./github_workflow.md
```
```{include} ./github_workflow_structure.md
```
```{include} ./gitlab_workflow.md
```
```{include} ./gitlab_pipeline_structure.md
```
```{include} ./advanced_variable_syntax.md
```
{% endif %}
