## Understanding Variable Substitution

YAML itself **cannot process or evaluate variables**.
But many **frameworks enable the use of variables**, like environment variables, within YAML files.
{% if page %}
This capability is essential for automation scripts in **GitHub** and **GitLab**, allowing for more complex and dynamic workflows.
{% endif %}

:::{card} The Usage of `$`
{% if page %}
In YAML, the `$` character has no special function and is treated as a regular character.
However, remote services like **GitHub** and **GitLab** use `$` to reference variables in YAML files, often for accessing environment variables.

The general approach consist of first substituting all `$<variable>` terms by the value of `<variable>` and then processing the resulting YAML script.

Additionally, **GitHub** introduces the {% raw %}`${{ ... }}`{% endraw %} syntax to dynamically evaluate expressions and variables.
{% else %}
**GitHub** and **GitLab** use **`$` to reference variables in YAML files**.

`$<varaible>` occurences are **substituted by the correspondng value** prior to processing the YAML file.
{% endif %}
:::
