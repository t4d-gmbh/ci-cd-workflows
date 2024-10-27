### Minimal Content of an Automation Script

A **GitLab** Pipeline must include at least the following elements:

{% if page %}
:::{admonition}
:class: note, margin
**GitLab** provides [a comprehensive overview](https://docs.gitlab.com/ee/ci/yaml/#keywords) of all top-level keys and their purpose.
:::
{% endif %}
:::{card} [`stages`](https://docs.gitlab.com/ee/ci/yaml/#stages)
A mandatory top-level key containing a list of strings, that identify the sequence of stages the Pipeline will sequentially run through.

Stages are processed sequentially and **define the order of job execution** in a **GitLab** Pipeline{% if page %}, helping to organize the workflow from start to finish{% endif %}.

{% if page %}

Each stage groups jobs that execute concurrently.
Stages allow you to manage the flow of your Pipeline, ensuring each step completes before moving on to the next.

You can choose the name of a stage freely, but some typical names are:

- **build**: Compile code, build binaries, or prepare artifacts.
- **test**: Run automated tests to ensure code quality.
- **deploy**: Deploy your application to staging or production.

Jobs in the next stage start only after the previous stage has completed successfully.
For more details on managing `stages`, refer to [GitLab's stages documentation](https://docs.gitlab.com/ee/ci/yaml/#stages).
{% endif %}

:::
:::{card} [`<job_name>`](https://docs.gitlab.com/ee/ci/yaml/#jobs)
**GitLab** identifies arbitrary top-level keys as a job, if they containt the key `script`.

Defined as top-level keys with **arbitrary names**, jobs are the individual tasks that make up a GitLab CI/CD pipeline.
{% if page %}
Jobs in GitLab run based on their assigned **stage** and can execute independently or sequentially within the pipeline.

Some essential properties for configuring jobs:

- **`script`**: Specifies the shell commands to run.
- **`stage`**: Defines the stage the job belongs to.
- **`only`/`except`**: Defines conditions for job execution (e.g., run only on specific branches).
- **`artifacts`**: Defines files to pass between jobs or to retain after a job completes.
- **`needs`**: Specifies dependencies with other jobs in the pipeline.
- **`rules`**: Advanced logic for conditional job execution.

Jobs in GitLab are flexible and allow extensive customization. Check [GitLab’s documentation on jobs](https://docs.gitlab.com/ee/ci/jobs/index.html) for more information.
{% endif %}
:::
{% if page %}
:::{note}
:class: margin
In the future the [`run`](https://docs.gitlab.com/ee/ci/yaml/#run) key might become an alternative to the `script` key.
:::
{% endif %}
:::{card} [`script`](https://docs.gitlab.com/ee/ci/yaml/index.html#script)
Is a mandatory key within a job.

`script` defines **a list of shell commands** that will be run sequentially when the job is executed.

{% if page %}
Each command in the `script` can be a single line or a multi-line block, allowing for complex operations to be performed during the job.

{% endif %}
:::
