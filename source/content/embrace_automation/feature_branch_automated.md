## Feature Branch Approach - with Automation

{% if page %}
The Feature Branch Approach has been a recurring subject, first in the [working-with-git](https://t4d-gmbh.github.io/working-with-git/content/feature_branch/index.html) course where we focus on the <i class="fab fa-git"></i>-side of things, then in [git-and-its-remotes](https://t4d-gmbh.github.io/git-and-its-remotes/content/project_management/index.html#feature-branch-approach-reloaded) we looked at how this approach can be carried out with remote service features, such as Issues, and Merge/Pull Requests.
Here now, we will focus on how automation can be integrated into this approach to streamline the workflow and help adhering to best practices.


In short, the Feature Branch Approach is a development strategy where individual features or enhancements are developed in isolated branches, allowing teams to work concurrently without affecting the healthy reference (i.e. the `main` branch in most cases) until the features are ready for integration.

During this process many event occur that could trigger a CI/CD workflow and we recommend that you identify those that are the most useful to the particular project and setup.

However, here we will provide some suggestions to get you started:
{% endif %}



{% if slide %}- **{% else %}#### {% endif %}Test the development branch{% if slide %}**{% endif %}
{% if page %}

You can setup tests to be triggered on all but the `main` branch, or any push event to a branch with an open Merge/Pull Request.
In doing so you can make sure that issues on the development branch are spotted early on.

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Report code coverage in the Merge/Pull Request{% if slide %}**{% endif %}
{% if page %}

Both **GitHub** and **GitLab** allow to (relatively) easily report the test coverage.
You can instruct the automation script performing the tests to also report the change in test coverage directly in the Merge/Pull Request.

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Perform linting checks on the development branch{% if slide %}**{% endif %}
{% if page %}

    On push to a development branch you can perform linting checks that will help to keep a well structured codebase during the development process of a feature.

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Test an anticipated merge commit{% if slide %}**{% endif %}
{% if page %}

When a Merge/Pull Request is no longer a draft, you can run an automation script that performs a merge (without committing it) of the feature branch, tests an reports the results.

This ensures that the merged code passes all tests before final integration.
Allow merging only if this test succeeds.

In **GitLab** such a test could look like this:

```yaml
# .gitlab-ci.yml
stages:
  - merge

variables:
  GIT_STRATEGY: fetch

merge_and_test:
  stage: merge
  script:
    - echo "Anticipating merge commit and testing..."
    - git fetch origin main
    - git checkout -b temp-merge-branch
    - git merge --no-commit origin/main
    - echo "Running tests after merge..."
    - # run your tests here
  rules:
    - if: '$CI_MERGE_REQUEST_ID && $CI_MERGE_REQUEST_DRAFT == "false"'
  when: manual  # Remove it the job should run automatically
```

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Perform a version increase upon merge{% if slide %}**{% endif %}
{% if page %}

You can setup and trigger a process that will create a new <i class="fab fa-git"></i> tag as soon as a feature branch is merged.
The process might fetch the latest tag, increase its minor version number by 1 and push a new tag, or you can use pre-existing tools, such as [semantic-release](https://github.com/semantic-release/semantic-release) for **GitHub** to perform that task for you.

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Cleanup branches after merge{% if slide %}**{% endif %}
{% if page %}

A good idea is to automate the cleanup of branches that are merged and no longer used.
```{tip}
This is also a relatively easy automation task to start with!
```

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Automate deployment to production or staging environment{% if slide %}**{% endif %}
{% if page %}
If you are working on a project that can somehow be deployed, like a static website that you want to deploy to [**GitHub**-](https://pages.github.com/) or [**GitLab**- pages](https://docs.gitlab.com/ee/user/project/pages/), you can setup a deployment script that runs on every update (i.e. `push`) to your healthy reference.

```{note}
The very content you are watching right now is depolyed just like this!
Checkout the [`pages.yml`](https://github.com/t4d-gmbh/ci-cd-workflows/blob/main/.github/workflows/pages.yml) Workflow to see how exactly this is done.
``
{% endif %}
