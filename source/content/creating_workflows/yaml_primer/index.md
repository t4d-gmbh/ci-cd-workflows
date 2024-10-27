## A YAML Primer

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./about_YAML
./syntax
./conclusion
```
{% else %}
```{include} ./about_YAML.md
```
```{include} ./syntax.md
```
```{include} ./conclusion.md
```
{% endif %}
