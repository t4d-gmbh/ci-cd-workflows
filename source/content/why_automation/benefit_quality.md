{% if page %}:::{card}{% else %}####{% endif %}  Increased Quality
- **Enforce Coding Standards**: {% if slide %}Formatting, naming conventions, code organization.{% else %}Automation tools can enforce coding standards, such as formatting, naming conventions, and code organization, ensuring that the codebase is consistent and easy to read.{% endif %}
- **Check code quality**: {% if slide %}Fode coverage, linting, quality metrics.{% else %}Automation tools can perform static code analysis, including checks for code coverage{% if page %}[^sn1]{% endif %}, linting{% if page %}[^sn2]{% endif %}, and other quality metrics, helping to identify and fix issues before they become problems.{% endif %}
{% if page %}
[^sn1]: _Code coverage_ measures the percentage of code that is executed during automated tests, helping to identify untested parts of the codebase.
[^sn2]: _Linting_ is the process of analyzing code for potential errors, stylistic issues, and adherence to coding standards.
:::
{% endif %}

{% if slide %}
::::{grid}
:::{grid-item-card} Linting Output
![Linting](./lint_example_output.png)
:::
:::{grid-item-card} Code Coverage Output 
![Code Coverage](./coverage_example_output.png)
:::
::::
{% endif %}
