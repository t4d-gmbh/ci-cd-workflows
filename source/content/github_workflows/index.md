## <i class="fab fa-github"></i> **GitHub** {octicon}`workflow` Workflows

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
