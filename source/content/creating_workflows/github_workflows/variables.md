### How to Define Variables for an Automation Script

**GitHub** enables the usage of variables in the definition of Workflows, furthermore, it provides a variety of [context variables](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs) that can be accessed using the {%raw%}`${{...}}`{%endraw%} syntax.

Some important contextual variables are:

- [**`github`**](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#github-context): Provides metadata about the Workflow run, Repository, and event that triggered the Workflow, etc.
- [**`vars`**](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#vars-context): Contains variables defined on Repository, Organization or Environment level.
  These variables [can be set via the Web-UI](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/store-information-in-variables#defining-variables-for-multiple-workflows).
:::{warning}
:class: margin
**`secrets` is the only acceptable place to store sensitive data!**
:::
- [**`secrets`**](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#secrets-context): Names and values of secrets that were defined for the Repository, Organization or Environment.
  Secrets are treated [in a particular way](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) by **GitHub** and can be set via the Web-UI.
{% if page %}
Refer to the official documentation for a [complete overview of **GitHub**'s contextual variables](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs) and [their availabilities](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#context-availability).

:::{admonition} Inspect context variables
:class: tip
Context variables are - as their name suggests - context dependant and it might not always be clear, what values are actually defined when a Workflow runs.

A straight forward way to debug context variables is to simply have their content returned by a job that runs in specific context:
{% raw %}
```yaml
jobs:
  list-github-context:
    runs-on: ubuntu-latest
    steps:
      - name: Print GitHub Context Variables
        env:
          GITHUB_CONTEXT: ${{ toJSON(github) }}
        run: |
          echo "GitHub context variables:"
          echo "$GITHUB_CONTEXT" | jq '.'
```
{% endraw %}
{% endif %}
:::
