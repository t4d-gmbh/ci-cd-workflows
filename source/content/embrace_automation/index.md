# 🤗 Embrace automation 🤗

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./how_to_trigger
./feature_branch_automated
./sensitive_data
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./how_to_trigger.md
```
```{include} ./feature_branch_automated.md
```
```{include} ./sensitive_data.md
```
{% endif %}
