# <i class="fas fa-person-running "></i> Runners <i class="fas fa-person-running fa-flip-horizontal"></i>

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./about
./configuration
./interaction
./security
./reproducibility
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./about.md
```
```{include} ./configuration.md
```
```{include} ./interaction.md
```
```{include} ./security.md
```
```{include} ./reproducibility.md
{% endif %}
