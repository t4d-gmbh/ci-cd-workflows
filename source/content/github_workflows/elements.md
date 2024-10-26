### Basic Elements

A **GitHub** Workflow must include at least the following core elements:

:::{note}
:class:margin
**GitHub** provides [a comprehensive overview](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions) of all top-level keys and their purpose.
:::

:::{card} [Triggers](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#on)
Are defined with the top-level key `on` and **determine when to initiate the workflow**{% if page %}, such as pushing code, opening a pull request, or creating an issue{% endif %}.

{% if page %}

Workflows in GitHub Actions can be triggered by:

- **Project events**: Actions like commits, pull requests, or issue creation.
- **External events**: Webhooks or APIs that signal GitHub to start a workflow.
- **Scheduled times**: Set workflows to run at regular intervals (e.g., nightly builds using cron syntax).
- **Manual triggers**: Start a workflow manually from the GitHub UI.

We recommend to [read about triggering events](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows) if you want to learn more about them.
{% endif %}

:::
:::{card} [Jobs](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#jobs)
Are defined with the top-level key `jobs` and **specify an environment along with a sequence of tasks** to perform.
{% if page %}
Jobs run in parallel by default and each job can contain a collection of tasks that are executed sequentially.

Some of the more relevant keys a job might contain:

- **`runs-on`**: Defines the type of machine (or VM) to run this job on.
- **`steps`**: Sequence of tasks to perform.
- **`needs`**: Establishes dependencies with other jobs.
- **`if`**: Allows to specify conditions to prevent a job from running.
- **`permissions`**: Modify the default permissions granted to the [GITHUB_TOKEN](https://docs.github.com/en/actions/security-for-github-actions/security-guides/automatic-token-authentication#permissions-for-the-github_token)

A full list can be found [here](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#jobs).
{% endif %}
:::
::::{card} [Steps](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions)
Are defined as lists for each job in the top level-key `jobs`, i.e. `jobs.<job_id>.steps`

Specify **individual commands or actions to be executed** as part of a job.
{% if page %}
Steps can either run shell commands or use [pre-built GitHub Actions](https://docs.github.com/en/actions/sharing-automations/creating-actions/about-custom-actions) to perform specific tasks.

Some keys an entry in `steps` might contain:

:::{margin}
:class: note
The keys `run` and `uses` cannot be used together.
:::
- **`if`**: Allows to specify conditions to prevent a step from running.
- **`run`**: A string that will be run as a shell command.
- **`uses`**: Specifies a pre-defined action to run. 
{% endif %}
::::
