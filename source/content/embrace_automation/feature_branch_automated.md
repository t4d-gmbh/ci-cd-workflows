## Feature Branch Approach - with Automation

{% if page %}
The Feature Branch Approach has been a recurring topic, first discussed in the [working-with-git](https://t4d-gmbh.github.io/working-with-git/content/feature_branch/index.html) course, where we focus on the <i class="fab fa-git"></i>-side of things. We also explored this approach in [git-and-its-remotes](https://t4d-gmbh.github.io/git-and-its-remotes/content/project_management/index.html#feature-branch-approach-reloaded), examining how it can be implemented using remote service features, such as Issues, and Merge/Pull Requests.
Here, we will focus on integrating automation into this approach to streamline workflows and adhere to best practices.


In short, the Feature Branch Approach is a development strategy where individual features or enhancements are developed in isolated branches. This allows teams to work concurrently without affecting the healthy reference (i.e. the `main` branch in most cases) until the features are ready for integration.

Throughout this process, various events may trigger a CI/CD workflow. We recommend identifying the events that are the most useful to your specific project and setup.

To help you get started, here are some suggestions:
{% endif %}



{% if slide %}- **{% else %}#### {% endif %}Test the development branch{% if slide %}**{% endif %}
{% if page %}

You can setup tests to be triggered on all branches except the `main` branch or for any push event to a branch with an open Merge/Pull Request.
By doing this, you can ensure that issues in the development branch are spotted early on.

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Report code coverage in the Merge/Pull Request{% if slide %}**{% endif %}
{% if page %}

Both **GitHub** and **GitLab** make it relatively easy report test coverage.
You can configure your automation script performing the tests to also report changes in test coverage directly within the Merge/Pull Request, providing valuable feedback to other collaborators.

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Perform linting checks on the development branch{% if slide %}**{% endif %}
{% if page %}

    Implement linting checks on the development branch (e.g., of a new feature) to enforce coding standards and catch potential issues before they merged into the main branch. This proactive approach can you can significantly improve code quality and maintenance.

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

You can setup a process that automatically creates a new <i class="fab fa-git"></i> tag as soon as a feature branch is merged.
This process might fetch the latest tag, increment its minor version number by 1, and push a new tag. Alternatively, you can use existing tools, such as [semantic-release](https://github.com/semantic-release/semantic-release) for **GitHub** to perform this task automatically for you.

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Cleanup branches after merge{% if slide %}**{% endif %}
{% if page %}
Automating the cleanup of branches that have been merged and are no longer needed is a good practice.
```{tip}
This is also a relatively easy automation task to start with!
```

{% endif %}
{% if slide %}- **{% else %}#### {% endif %}Automate deployment to production or staging environment{% if slide %}**{% endif %}
{% if page %}
If you are working on a project that can be deployed, like a static website in [**GitHub**-](https://pages.github.com/) or [**GitLab**- pages](https://docs.gitlab.com/ee/user/project/pages/), you can setup a deployment script that runs on every update (i.e., `push`) to your healthy reference.

```{note}
The very content you are watching right now is depolyed in this manner!
Checkout the [`pages.yml`](https://github.com/t4d-gmbh/ci-cd-workflows/blob/main/.github/workflows/pages.yml) Workflow to see how exactly this is done.
``
{% endif %}
