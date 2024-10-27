### How to Trigger an Automation Script
{% if slide %}
- **Event Triggers:**
  - A variety of events can trigger a Workflow in **GitHub**.
  - Each Workflow (YAML file in `.github/workflows/`) must include the top-level key `on`.

- **Job and Step Conditions:**
  - Individual jobs (under the `jobs` key) and specific steps (under the `steps` key) can use the `if` key.
  - The `if` key allows for setting conditions to skip particular jobs or steps.

- **Skipped Job Status:**
  - If a Workflow runs and a job is skipped, its status will be updated to `skipped`.

{% else %}
In **GitHub**, [a variety of events can trigger a Workflow](https://docs.github.com/en/actions/writing-workflows/choosing-when-your-workflow-runs/events-that-trigger-workflows), and each Workflow (i.e., each YAML file located in `.github/workflows/`) must include the top-level key `on`, which specifies the events that will activate this Workflow.

Additionally, individual jobs (i.e., entries under the top-level key `jobs`) and specific steps (i.e., elements within the `steps` key of a job) can utilize the `if` key to set conditions for skipping that particular step or job.
However, it's important to note that if a Workflow runs and a job is skipped, its status will be updated to `skipped`.

A conditional job could look like this:
{%raw%}
```yaml
name: example-workflow
on: [push]
jobs:
  conditional-greet:
    if: ${{ github.repository == 'myuser/myrepo' }}
    runs-on: ubuntu-latest
    steps:
      - run: echo "Howdie!"
```
{%endraw%}
{% endif %}
