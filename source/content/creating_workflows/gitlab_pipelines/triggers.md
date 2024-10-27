### How to Trigger an Automation Script
{% if slide %}
- **Triggering Pipelines:**
  - Pipelines can be triggered by various events.
  - Rules can be set to determine if an event should initiate actions.

- **Defining Pipeline Rules:**
  Use the `rules` key under the top-level `workflow` key to define rules for the entire Pipeline.
  ```yaml
  workflow:
    rules:
      - if: $CI_PIPELINE_SOURCE == "merge_request_event"
  ```

- **Defining Job Rules:**
  The `rules` keyword can also be used for individual jobs.
  ```yaml
  job1:
    script:
      - echo "This is a merge request"
    rules:
      - if: $CI_PIPELINE_SOURCE == "merge_request_event"
  ```
{% else %}
In **GitLab**, [Pipelines can be triggered by various events](https://docs.gitlab.com/ee/ci/pipelines/), and you have the option to set rules that determine whether an event should initiate any action, both at the Pipeline level and for each individual job.

To define rules for the entire Pipeline, they must be placed under the `rules` key within the top-level key `workflow`.

An example rule to trigger a Pipeline on a Merge Request would look like this:
```yaml
workflow:
  rules:
    - if: $CI_PIPELINE_SOURCE == "merge_request_event"
```

For individual jobs, the `rules` keyword can also be utilized to specify whether an event should trigger that particular job.

An example rule to trigger a job on a Merge Request would look like this:
```yaml
job1:
  script:
    - echo "This is a merge request"
  rules:
    - if: $CI_PIPELINE_SOURCE == "merge_request_event"
```
{% endif %}
