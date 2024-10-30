### How to Define Variables for an Automation Script

**GitHub** allows the use of variables in Workflows definitions and provides a variety of [context variables](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs) that can be accessed using the {%raw%}`${{...}}`{%endraw%} syntax.

Some important contextual variables include:

- [**`github`**](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#github-context): Provides metadata about the Workflow run, Repository, and event that triggered the Workflow, etc. 
  - E.g. `github.event_name` indicates the name of the event that triggered the Workflow (e.g. `push`, `pull_request`, etc.) while `github.repository` provides the name of the Repository.
- [**`vars`**](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#vars-context): Contains variables defined at the Repository, Organization or Environment level. 
  These variables [can be set via the Web-UI](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/store-information-in-variables#defining-variables-for-multiple-workflows). 
  - For instance, `vars.my_variable` represents a variable named `my_variable`.
:::{warning}
:class: margin
Sensitive data should be stored outside of **GitHub**!
**`secrets` is the only half-way acceptable place to store sensitive data!**
:::
- [**`secrets`**](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#secrets-context): contains the names and values of secrets defined for the Repository, Organization or Environment.
  Secrets are handled [in a specific way](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) by **GitHub** and can be set via the Web-UI. 
  - For example, `secrets.TOKEN` refers to a secret named `TOKEN`.

{% if page %}
Refer to the official documentation for a [complete overview of **GitHub**'s contextual variables](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs) and [their availability](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#context-availability).

:::{admonition} Inspect context variables
:class: tip
Context variables are, as their name suggests, context-dependent, and it may not always be clear what values are actually defined when a Workflow runs.

A straightforward way to debug context variables is to simply have their content returned by a job that runs in specific context:
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
