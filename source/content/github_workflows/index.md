## <i class="fab fa-github"></i> **GitHub** {octicon}`workflow` Workflows

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./example
./defining
./elements
./workflows
./evaluation
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./example.md
```
```{include} ./defining.md
```
```{include} ./elements.md
```
```{include} ./workflows.md
```
```{include} ./evaluation.md
```
{% endif %}
