# Creating CI/CD Scripts

Both <i class="fab fa-github"></i> **GitHub** and <i class="fab fa-gitlab"></i> **GitLab** use [YAML](https://yaml.org/) to define CI/CD scripts.

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./yaml_primer/index
./using_variables
./github/index
./gitlab/index
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./yaml_primer/index.md
```
```{include} ./yaml_primer/about_YAML.md
```
```{include} ./yaml_primer/syntax.md
```
```{include} ./yaml_primer/conclusion.md
```
```{include} ./using_variables.md
```
{% endif %}
