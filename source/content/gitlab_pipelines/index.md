## <i class="fab fa-gitlab"></i> **GitLab** {octicon}`workflow` Pipelines

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./example
./defining
./workflows
./evaluation
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./example.md
```
```{include} ./defining.md
```
```{include} ./workflows.md
```
```{include} ./evaluation.md
```
{% endif %}

