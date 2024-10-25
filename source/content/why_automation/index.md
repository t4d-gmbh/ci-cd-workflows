# Why 🤖 Automation?

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./cicd
./benefits
./for_non_sd
./automation_in_remotes
./how_it_helps
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./cicd.md
```
```{include} ./benefits.md
```
```{include} ./benefit_healthy_ref.md
```
```{include} ./benefit_collab.md
```
```{include} ./benefit_quality.md
```
```{include} ./benefit_transparency.md
```
```{include} ./benefit_reproducibility.md
```
```{include} ./for_non_sd.md
```
```{include} ./automation_in_remotes.md
```
```{include} ./how_it_helps.md
```
{% endif %}
