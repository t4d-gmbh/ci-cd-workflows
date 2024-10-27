# <i class="fas fa-person-running "></i> Runners <i class="fas fa-person-running fa-flip-horizontal"></i>

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./what_are_runners
./runner_types
./configuring_runners
./communication_with_remote
./some_considerations
./configuration
./interaction
./security
./reproducibility
```
{% else %}
<!-- BUILDING THE PAGES -->
```{include} ./what_are_runners.md
```
```{include} ./runner_types.md
```
```{include} ./configuring_runners.md
```
```{include} ./communication_with_remote.md
```
```{include} ./some_considerations.md
```
```{include} ./configuration.md
```
```{include} ./interaction.md
```
```{include} ./security.md
```
```{include} ./reproducibility.md
```
{% endif %}
