## Overview <i class="fab fa-github"></i> Workflows & <i class="fab fa-gitlab"></i>  Pipelines

| Feature                     | <i class="fab fa-github"></i> Workflows                          | <i class="fab fa-gitlab"></i>  Pipelines                          |
|-----------------------------|------------------------------------------|-------------------------------------------|
| **Definition Location**      | Jobs are defined under the `jobs` key   | Jobs are defined as top-level keys        |
| **Job Structure**           | Each job contains a list of `steps`     | Each job has a single `script` key that can take a list of CLI commands |
| **Triggers**                | Uses `on` to specify events (e.g., push, pull request) | Uses `only`, `except`, or `rules` to specify when jobs run |
| **Environment Variables**   | Defined in `env` at job or workflow level | Defined in `variables` at job or pipeline level |
| **Matrix Builds**           | Supports matrix builds using `strategy` | Supports matrix builds using `parallel` |
| **Artifacts**               | Artifacts are defined in `jobs` using `artifacts` key | Artifacts are defined in `artifacts` key within jobs |
| **Caching**                 | Caching is defined in `jobs` using `cache` key | Caching is defined in `cache` key within jobs |
| **Conditional Execution**   | Uses `if` condition for job execution    | Uses `rules` or `only/except` for job execution |
| **UI Integration**          | Integrated with GitHub Actions UI       | Integrated with GitLab CI/CD UI          |
| **YAML File Location**      | `.github/workflows/` directory           | `.gitlab-ci.yml` file in the root directory |
