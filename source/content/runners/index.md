# <i class="fas fa-person-running "></i> Runners <i class="fas fa-person-running fa-flip-horizontal"></i>

{% if build == "slides" %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./what_are_runners
./runner_types
./configuring_runners
./communication_with_remote
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
{% endif %}
