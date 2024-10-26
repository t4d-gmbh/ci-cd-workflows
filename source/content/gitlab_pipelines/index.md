## <i class="fab fa-gitlab"></i> **GitLab** {material-outlined}`account_tree` Pipelines

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

