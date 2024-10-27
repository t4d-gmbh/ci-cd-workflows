## Understanding Variable Substitution

YAML itself **cannot process or evaluate variables**.
But many **frameworks enable the use of variables**, like environment variables, within YAML files.
{% if page %}
This capability is essential for automation scripts in **GitHub** and **GitLab**, allowing for more complex and dynamic workflows.
{% endif %}

::::{card} The Usage of `$`
{% if page %}
In YAML, the `$` character has no special function and is treated as a regular character.
However, remote services like **GitHub** and **GitLab** use `$` to reference variables in YAML files, often for accessing environment variables.

The general approach consist of first substituting all `$<variable>` terms by the value of `<variable>` and then processing the resulting YAML script.

{% else %}
**GitHub** and **GitLab** use **`$` to reference variables in YAML files**.

`$<varaible>` occurrences are **substituted by the corresponding value** prior to processing the YAML file.
{% endif %}
:::{note}
**GitHub** also uses the {% raw %}`${{...}}`{% endraw %} syntax that can [evaluate expressions](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/evaluate-expressions-in-workflows-and-actions), like scoped variables.

{% if page %}
- This functionality is a custom tool of **GitHub** and not to be confused with templating languages like [Jinja](https://jinja.palletsprojects.com/en/stable/).
- You will use this syntax to access predefined namespaces - or contexts in the **GitHub** lingo - like the `secrets` context which can hold secrets that were set for the Organization, or Repository via the Web-UI.
- **GitHub** provides a set of [custom functions](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/evaluate-expressions-in-workflows-and-actions#functions) can can be evaluated within a {%raw%}`${{...}}`{%endraw%} clause.
{% endif %}
:::
::::
