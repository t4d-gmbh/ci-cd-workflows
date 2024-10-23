# A YAML Primer

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./about_YAML
./syntax
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./about_YAML.md
```
```{include} ./syntax.md
```
## Conclusion

YAML's straightforward syntax and structure make it an ideal choice for configuration files in CI/CD workflows. Its readability enhances collaboration among developers, making it easier to define and manage complex workflows in GitHub and GitLab.
{% endif %}
