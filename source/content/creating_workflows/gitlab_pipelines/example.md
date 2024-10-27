### Example


{% if page %}An exemplary <i class="fab fa-gitlab"></i> Pipeline file could look like this:{% endif %}

```yaml
# .gitlab-ci.yml
stages:
  - build
  - test

build_job:
  stage: build
  script:
    - echo "Building the project..."

test_job:
  stage: test
  script:
    - echo "Running tests..."
```
