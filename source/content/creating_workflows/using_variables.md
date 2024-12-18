## Understanding Variable Substitution

YAML itself **cannot process or evaluate variables**.
However, many **frameworks**, such as in **GitHub** and **GitLab** allow the use of variables - environment variables - within YAML files {% if page %} which is crucial for automation scripts. {% endif %}

:::::{card} The Usage of `$`
{% if page %}
In YAML, `$` is just a regular character.
However, remote services like **GitHub** and **GitLab** use `$` to reference variables in YAML files, often for accessing environment variables.

The general approach consist of first substituting all `$<variable>` terms by the value of `<variable>` and then processing the resulting YAML script.

{% else %}
**GitHub** and **GitLab** use `$` to **reference variables in YAML files**.

`$<variable>` occurrences are **substituted by the corresponding value** prior to processing the YAML file.
{% endif %}
::::{admonition} Example
:class: tip
```yaml
script:
  - BRANCH=$CI_COMMIT_BRANCH
```
::::
::::{note}
**GitHub** also uses the {% raw %}`${{...}}`{% endraw %} syntax that can [evaluate expressions](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/evaluate-expressions-in-workflows-and-actions), like scoped variables.

{% if page %}
- This functionality is a custom tool of **GitHub** and not to be confused with templating languages like [Jinja](https://jinja.palletsprojects.com/en/stable/).
- You will use this syntax to access predefined namespaces - or contexts in the **GitHub** lingo - like the `secrets` context which can hold secrets that were set for the Organization, or Repository via the Web-UI.
- **GitHub** provides a set of [custom functions](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/evaluate-expressions-in-workflows-and-actions#functions) can can be evaluated within a {%raw%}`${{...}}`{%endraw%} clause.
:::{admonition} Example
:class: tip
{%raw%}
```yaml
env:
 BRANCH_NAME: ${{ github.head_ref || github.ref_name }} 
```
{%endraw%}
:::

{% endif %}
::::
:::::
