### How to Handle Automation Scripts

{% if slide %}
The file **`.gitlab-ci.yml`** defines the **"main" Pipeline for a Project**.

It must:

- Be under version control,
- Have a `.yml` or `.yaml` extension,
- Reside in the root directory of the repository.
{% else %}In **GitLab**, a Project has one central YAML file to configure automation, the **`.gitlab-ci.yml`** file.
This file needs to be **under version control** and must **reside in the root directory** of the <i class="fab fa-git"></i> repository{% endif %}
{% if slide %}

:::{note}
It is possible to [run "child" Pipelines](https://docs.gitlab.com/ee/ci/pipelines/pipeline_architectures.html#parent-child-pipelines), but the "main" Pipeline is always initiated with the `.gitlab-ci.yml` file.
:::
{% else %}
Although **GitLab** considers only the `.gitlab-ci.yml` file for defining the "main" Pipeline, you can still set up multiple pipelines.
This can be achieved by establishing conditions for the individual steps within the main Pipeline or by [including "child" Pipelines](https://docs.gitlab.com/ee/ci/pipelines/pipeline_architectures.html#parent-child-pipelines).
{% endif %}

