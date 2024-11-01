## <i class="fab fa-github"></i> Workflows vs. <i class="fab fa-gitlab"></i> Pipelines - by Example
::::{grid}
:::{grid-item-card} <i class="fab fa-github"></i>
```yaml
# .github/workflows/hello_world.yml

on: push

jobs:
  say_hello:
    steps:
      - run: echo "Hello, World!"
```
:::
:::{grid-item-card} <i class="fab fa-gitlab"></i>
```yaml
# .gitlab-ci.yml

stages:
  - greet

greet_job:
  stage: greet
  script:
    - echo "Hello, World!"
```
:::
