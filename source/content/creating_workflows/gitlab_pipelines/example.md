### Minimal Automation Script

{% if page %}An minimal exemplary <i class="fab fa-gitlab"></i> Pipeline file could look like this:{% endif %}

```yaml
# .gitlab-ci.yml

stages:
  - greet

greet_job:
  stage: greet
  script:
    - echo "Hello, World!"
```
