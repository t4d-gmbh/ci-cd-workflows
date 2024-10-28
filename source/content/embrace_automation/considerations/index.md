## Some considerations

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./own_docker
./debugging
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./own_docker.md
```
```{include} ./debugging.md
```
{% endif %}

