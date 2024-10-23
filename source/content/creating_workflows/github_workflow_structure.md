### <i class="fab fa-github"></i> **GitHub** {octicon}`workflow` Workflows

- **GitHub Actions**: In GitHub, workflows are defined in `.github/workflows/` directory using YAML files. These files specify the events that trigger the workflow, the jobs to run, and the steps within each job.
  ```yaml
  name: CI

  on: [push]

  jobs:
    build:
      runs-on: ubuntu-latest
      steps:
        - name: Checkout code
          uses: actions/checkout@v2
        - name: Run tests
          run: npm test
  ```
