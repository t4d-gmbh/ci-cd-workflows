### Debugging CI/CD Pipelines/Workflows
{% if page %}
When you start creating your own automation scripts, you'll find that debugging them is more challenging than debugging local code.
This is partly because your YAML scripts are triggered by specific events that may not happen on demand.
Additionally, both GitLab and GitHub offer a wide range of context-dependent variables that can complicate the debugging process.
{% endif %}
A good approach for debugging is:

- Debug the triggering process and the actual actions the script performs separately.
- Choose an easy trigger to debug a Pipeline/Workflow (e.g. on push to a development branch).
- Use `echo` statements to inspect variables.

:::{admonition} Inspect <i class="fab fa-github"></i> context variables 
:class: tip
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
:::
