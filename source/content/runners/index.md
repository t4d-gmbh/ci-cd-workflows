# <i class="fas fa-person-running "></i> Runners <i class="fas fa-person-running fa-flip-horizontal"></i>

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./slide1
```
{% else %}
<!-- BUILDING THE PAGES -->
### some sub title
```{include} ./slide1.md
```
{% endif %}
