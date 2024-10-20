# Exercise

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./problem
```
{% else %}
<!-- BUILDING THE PAGES -->
### some sub title
```{include} ./problem.md
```
{% endif %}

