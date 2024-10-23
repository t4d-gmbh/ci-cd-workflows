### <i class="fab fa-gitlab"></i> **GitLab** {octicon}`workflow` Pipelines

- **GitLab CI/CD**: In GitLab, pipelines are defined in a `.gitlab-ci.yml` file at the root of the repository. This file outlines the stages, jobs, and scripts to execute.
  ```yaml
  stages:
    - build
    - test

  build_job:
    stage: build
    script:
      - echo "Building the project..."

  test_job:
    stage: test
    script:
      - echo "Running tests..."
  ```


