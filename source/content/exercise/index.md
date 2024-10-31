# Exercise

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./problem
```
{% else %}
<!-- BUILDING THE PAGES -->

```{include} ./problem.md
```
{% endif %}

