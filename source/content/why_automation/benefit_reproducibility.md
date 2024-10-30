{% if page %}:::{card}{% else %}####{% endif %} Reproducibility
- **Scripted Processes**: {% if slide %}Transparently define processes like data cleaning, processing, or visualization.{% else %}Automation scripts transparently define processes, like data cleaning, processing, visualization, simulations or other types of analysis.{% endif %}
- **Track Processes Execution**: {% if slide %}Ensure consistent and reproducible results.{% else %}By linking process execution to project states, automation ensures consistent and reproducible results.{% endif %}
- **Consistent Environments**: {% if slide %}Integrate tools like Docker into automated workflows.{% else %}Tools like _Docker_ can be integrated into automated workflows, allowing developers to define and replicate environments easily, enhancing reproducibility.{% endif %}
{%if page %}:::{% endif %}
