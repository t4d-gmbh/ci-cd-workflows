## <i class="fab fa-gitlab"></i> **GitLab** {octicon}`workflow` Pipelines

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./workflows
./structure
./evaluation
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./workflows.md
```
```{include} ./structure.md
```
```{include} ./evaluation.md
```
{% endif %}

