{% if page %}:::{card}{% else %}####{% endif %} Transparency
- **Visibility into Workflows**: {% if slide %}Transparent testing, building, and deploying procedures.{% else %}Automation scripts transparently define testing, building and deploying procedures, providing end-to-end visibility and insight.{% endif %}
- **Visibility into Process States**: {% if slide %}Updated insights into the status of build, test, deployment or other processes.{% else %}Automated pipelines and dashboards provide updated insights into the status of builds, tests, deployments and other type of processes, making it easier for stakeholders to understand project progress.{% endif %}
{%if page %}:::{% endif %}

{% if slide %}
:::{grid}
:::{grid-item-card} 
![Transparent Reporting Status Badges](./status_badge_example.png)
:::
:::
{% endif %}
