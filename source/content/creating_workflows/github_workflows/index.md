## <i class="fab fa-github"></i> **GitHub** {octicon}`workflow` Workflows

How to create an automation script in **GitHub**

_Or at least how to get started..._

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./location
./content
./example
./triggers
./variables
./advanced
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./location.md
```
```{include} ./content.md
```
```{include} ./example.md
```
```{include} ./triggers.md
```
```{include} ./variables.md
```
---
```{include} ./advanced.md
```
{% endif %}
