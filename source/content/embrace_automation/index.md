# 🤗 Embrace automation 🤗

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
