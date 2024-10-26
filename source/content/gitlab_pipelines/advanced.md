### Advanced Features

{% if slide %}- {% else %}:::{card}{% endif %} **Pipeline Triggers**{% if page %}:

While in **GitLab** [single jobs can be triggered via rules](https://docs.gitlab.com/ee/ci/yaml/#rules) it is also possible to set rules for the entire Pipeline using the [top-level keyword `workflow`](https://docs.gitlab.com/ee/ci/yaml/#workflow).

```yaml
workflow:
  rules:
    - if: $CI_COMMIT_TITLE =~ /-draft$/
      when: never
    - if: $CI_PIPELINE_SOURCE == "merge_request_event"
```
In fact, with `workflow` you can control more than just when the Pipeline should be, for example also when it should be canceled. 

_Read more about [controlling the Pipeline behaviour with `workflow`](https://docs.gitlab.com/ee/ci/yaml/workflow.html)._
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using Variables**{% if page %}:

**GitLab** provides [predefined variables](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html#predefined-variables) that provide information on things like:

- [`CI_PIPELINE_SOURCE`](https://docs.gitlab.com/ee/ci/jobs/job_rules.html#ci_pipeline_source-predefined-variable): Indicates how the Pipeline was triggered.
- `CI_PROJECT_ID`: The ID of the related project.
- ...

**GitLab** allows you to define and use [variables](https://docs.gitlab.com/ee/ci/yaml/#variables) in Pipelines, both on the top level and within a job:

```yaml
variables:
  GLOBAL_VAR: "I'm global"

job1:
  variables:
    SOME_VAR: "I'm local"
  script:
    - echo "Variables - '$GLOBAL_VAR' and - '$SOME_VAR'"

job2:
  script:
    - echo "Variables '$GLOBAL_VAR' and '$SOME_VAR'"  # SOME_VAR will be ''
```

In addition you can [set variables in the UI](https://docs.gitlab.com/ee/ci/variables/#define-a-cicd-variable-in-the-ui), which is **the recommended approach to store sensitive information**, like access tokens or password.
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using `before_script` and `after_script`**{% if page %}:

You can define commands that run before or after the main `script` commands even if the `scirpt` command fails or times out.

```yaml

job_name:
  before_script:
    - echo "This runs before the main script"
  script:
    - echo "This is the main script"
  after_script:
    - echo "This runs after the main script"
```

_Read more about [before_script](https://docs.gitlab.com/ee/ci/yaml/#before_script) and [after_script](https://docs.gitlab.com/ee/ci/yaml/#after_script)._
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Setting Defaults**{% if page %}:

The [top-level key `default`](https://docs.gitlab.com/ee/ci/yaml/#default) can be used to set values and behaviours that will apply to all jobs, unless overwritten directly.

Some Candidates for defaults are:

- `after_script`: Commands to run after `script`
- `before_script`: Commands to run before `script`
- `tags`: Set of tags to select a runner
- `image`: The Docker image to use
- `timeout`: Maximal runtime of a job
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Creating Dependent Jobs**{% if page %}:

You can define job dependencies using [the `needs` keyword](https://docs.gitlab.com/ee/ci/yaml/#needs), ensuring that jobs run in sequence even within the same stage.

```yaml
test1:
  stage: test
  script:
    - echo "Running test 1"
test2:
  stage: test
  needs: ["test1"]
  script:
    - echo "Running test 2"
```
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Parallel Execution**{% if page %}:

You can run a job multiple times optionally with different configurations (e.g., testing across different versions of a programming language).

```yaml
test:
  parallel:
    matrix:
      - python_version: [3.7, 3.8, 3.9]
  script:
    - echo "Testing with Python version $python_version"
```
_Read more about [the parallel keyword](https://docs.gitlab.com/ee/ci/yaml/#parallel)._
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Caching Dependencies**{% if page %}:

Caching is a key feature to create fast pipelines and reduce computational overhead.

The [job keyword cache]() can be used to determine what should be cached in a job.

```yaml
build:
  script:
    - echo "Hello" >> hello.txt
  cache:
    paths:
      - hello.txt
```
_Read more about [Caching](https://docs.gitlab.com/ee/ci/caching/index.html)._
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using Services**{% if page %}:

If your job requires a service like a database, you can **define service containers that will run alongside** the job.

```yaml
test:
  services:
    - name: postgres:12
      alias: db
      entrypoint: ["/usr/local/bin/db-postgres"]
      command:
        - start
  script:
    - echo "Tests with PostgreSQL"
```
Read more about [services in the **GitLab** documentation](https://docs.gitlab.com/ee/ci/yaml/#services).
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using Tags (Targeting Runners)**{% if page %}:

You can specify which runners to use for a job based on the runner's tags.

```yaml
job_name:
  tags:
    - docker
  script:
    - echo "Running on a runner with the 'docker' tag"
```
```{note}
These tags are **not in any way related** to <i class="fab fa-git"></i> tags.
```
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Reusing Configurations**{% if page %}:

Use [YAML anchors](https://docs.gitlab.com/ee/ci/yaml/yaml_optimization.html#anchors) to reuse configurations across jobs.

```yaml
.default_script: &default_script
  - echo "This is a default job template"

job1:
  script:
    - *default_script
    - echo "This is job 1, extending the default script


.job_template: &job_default  # .job_template is hidden
  image: ruby:2.6
  services:
    - postgres

job2:
  <<: *job_default
  script:
    - echo "This is job 2, extending the default job template"
```
:::{% endif %}
