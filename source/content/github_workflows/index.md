## <i class="fab fa-github"></i> **GitHub** {octicon}`workflow` Workflows

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./example
./defining
./elements
./advanced
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
```{include} ./advanced.md
```
```{include} ./evaluation.md
```
{% endif %}
