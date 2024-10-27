### How to Handle Automation Scripts

{% if slide %}
A YAML file that defines a <i class="fab fa-github"></i> Workflow must:

- be under version control;
- have a `.yml` or `.yaml` extension;
- reside in the **`.github/workflows/`** folder;
{% else %}Automation scripts for **GitHub** should be included in the <i class="fab fa-git"></i> repository and **must be located in the `.github/workflows/` directory**.{% endif %}
{% if slide %}
- can be arbitrarily named;

:::{note}
If multiple YAML files reside under `.github/workflows/`, **each one is treated as an individual Workflow**.
:::
{% else %}You can name the YAML files as you prefer, and you are free to add multiple files to the `.github/workflows/` directory, enabling you to associate several Workflows with a single Project.
Each file in that directory is treated as a separate definition of a Workflow.
This is an excellent method for sharing complete workflows across projects; simply copy the relevant YAML file.
{% endif %}
