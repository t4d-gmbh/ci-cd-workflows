### How to Define Variables for an Automation Script

**GitLab** allows the use of variables in the definition of Pipelines and provides a variety of [predefined variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html).

We can differentiate between:

- **Predefined Variables:** 
  {% if page %}GitLab provides a set of [predefined variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html) that are automatically available in your Pipeline jobs.{% endif %}
  These variables typically start with `CI_...` and contain information about the Project, Pipeline, job, and more.

:::{warning}
:class: margin
Sensitive data should be stored outside of **GitLab**!
**Half-way acceptable is to use [protected and masked custom variables](https://docs.gitlab.com/ee/ci/pipelines/pipeline_security.html)**
:::
  
- **Custom Variables:**
  {% if page %}You can define [custom variables](https://docs.gitlab.com/ee/ci/variables/#gitlab-ci-cd-variables) at the Project, Group, or Subgroup level.{% endif %}
  These variables can be set via the Web-UI and can be used to store configuration values or secrets that your jobs need to access.
{% if page %}

An exemplary use of a predefined variable:
{% endif %}
```yaml
myjob:
  stage: test
  script:
    - echo "This job run in stage: '$CI_JOB_STAGE'"
```
{% if page %}
Refer to the official documentation for a [complete overview of **GitLab**'s predefined variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html) and [their availability](https://docs.gitlab.com/ee/ci/variables/#predefined-variables).
{% endif %}
