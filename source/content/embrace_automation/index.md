# 🤗 Embrace automation 🤗

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./recap
./feature_branch_automated
./considerations/index
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./recap.md
```
```{include} ./feature_branch_automated.md
```
```{include} ./considerations/index.md
```
```{include} ./considerations/own_docker.md
```
{% endif %}
