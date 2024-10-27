### Defining <i class="fab fa-gitlab"></i> Pipelines

- **Location**: Pipelines are configured in a single YAML file `.gitlab-ci.yml`
- **Multiple Pipelines**: To run multiple pipelines you can either **trigger "child" Pipelines** or **implement rules for conditional Pipelines**.
{% if page %}
  For example:
  - **Building and testing code** for each pull request submission.
  - **Deploying your application** when a new version is released.
  - **Automating issue management** by adding labels to new issues.
{% endif %}
