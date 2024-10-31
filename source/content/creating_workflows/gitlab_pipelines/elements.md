### Basic Elements

A **GitLab** Pipeline must include at least the following core elements:

:::{admonition}
:class: note, margin
**GitLab** provides [a comprehensive overview](https://docs.gitlab.com/ee/ci/yaml/#keywords) of all top-level keys and their purpose.
:::

:::{card} [Stages](https://docs.gitlab.com/ee/ci/yaml/#stages)
List defined with the top-level key `stages`, these **define the order of job execution** in a **GitLab** Pipeline{% if page %}, helping to organize the workflow from start to finish{% endif %}.

{% if page %}

Each stage groups jobs that execute concurrently. Stages allow you to manage the flow of your pipeline, ensuring each step completes before moving on to the next.

Common stages include:

- **Build**: Compile code, build binaries, or prepare artifacts.
- **Test**: Run automated tests to ensure code quality.
- **Deploy**: Deploy your application to staging or production.

Jobs in the next stage start only after the previous stage is completed successfully. For more details on managing pipeline stages, refer to [GitLab's stages documentation](https://docs.gitlab.com/ee/ci/yaml/#stages).
{% endif %}

:::
:::{card} [Jobs](https://docs.gitlab.com/ee/ci/yaml/#jobs)
are top-level keys with **arbitrary names**. Jobs are the individual tasks that make up a GitLab CI/CD pipeline.
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
:::{card} [Script](https://docs.gitlab.com/ee/ci/yaml/index.html#script)
The `script` key is used to define the commands that will be executed as part of a job in **GitLab** CI/CD.

Specify **a list of shell commands** that will be run sequentially when the job is executed.
{% if page %}
Each command in the `script` can be a single line or a multi-line block, allowing for complex operations to be performed during the job.

{% endif %}
:::
