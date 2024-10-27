### Minimal Content of an Automation Script

A **GitHub** Workflow must include at least the following elements (keys):

{% if page %}
:::{note}
:class: margin
**GitHub** provides [a comprehensive overview](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions) of all top-level keys and their purpose.
:::
{% endif %}
:::{card} [`on`](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#on)
Is a mandatory top-level key that **determines when to initiate the Workflow**{% if page %}, such as when pushing code, opening a pull request, or creating an issue{% endif %}.

{% if page %}

Workflows in **GitHub** can be triggered by:

- **Repository events**: Like  commits, pull requests, or issue creation, e.g. `on: create` or `on: [push, fork]`.
- **External events**: Webhooks or APIs that signal **GitHub** to start a Workflow.
- **Scheduled times**: Set Workflows to run at regular intervals (e.g., nightly builds using cron syntax).
- **Manual triggers**: Start a Workflow manually from the GitHub UI.

We recommend to [read about triggering events](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows) if you want to learn more about them.
{% endif %}

:::
:::{card} [`jobs`](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#jobs)
Is a top-level key that holds a dictionary of jobs, each **specify an environment along with a sequence of `tasks`** to perform.
{% if page %}
Jobs can be arbitrarily named (i.e. the key an be set freely).
They will run in parallel by default and each job can contain a collection of `steps` that are executed sequentially.

Some of the more relevant keys a job might contain:

- **`runs-on`**: Defines the type of machine (or VM) to run this job on.
- **`steps`**: Sequence of tasks to perform.
- **`needs`**: Establishes dependencies with other jobs.
- **`if`**: Allows to specify conditions to prevent a job from running.
- **`permissions`**: Modify the default permissions granted to the [GITHUB_TOKEN](https://docs.github.com/en/actions/security-for-github-actions/security-guides/automatic-token-authentication#permissions-for-the-github_token)

`jobs` might look like this:
{% raw %}
```yaml
jobs:
  my-job:
    name: My Job
    runs-on: ubuntu-latest
    steps:
      - name: Print a greeting
        uses: actions/checkout@v3
      - name: Print a greeting
        run: |
          echo ${{ github.repository }}
```
{% endraw %}
A full list of keys a job accepts can be found [here](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions#jobs).
{% endif %}
:::
::::{card} [`steps`](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions)
Is a mandatory key within a job.
`steps` defines a list of **individual commands or actions to be executed** as part of a job.
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
