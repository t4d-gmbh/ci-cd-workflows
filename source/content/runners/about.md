## What Are Runners?

**Runners** are the underlying infrastructure that executes jobs in your automation setup.
They are can by physical machines, virtual machines or containers responsible for executing the steps defined in your <i class="fab fa-github"></i> Workflow or <i class="fab fa-gitlab"></i> Pipeline configuration file.
A runner can reside in the

Both **GitHub** and **GitLab** know Runners, and they works work in a similar way but with some platform-specific differences.

---

### GitHub Actions Runners

#### What is a GitHub Actions Runner?

A **GitHub Actions runner** is a virtual environment that runs the jobs specified in your `.github/workflows` YAML file. Runners can either be **hosted by GitHub** (GitHub-hosted runners) or **self-hosted** (you provide your own infrastructure).

- **GitHub-hosted runners**: GitHub provides and manages virtual machines pre-configured with commonly used tools and environments (e.g., Ubuntu, macOS, Windows).
- **Self-hosted runners**: You can provide and configure your own machines to run the jobs. This gives you more control and customization over the environment and machine capacity.

#### How Do GitHub Runners Work?

When a workflow is triggered, GitHub sends the job to a runner based on the specified `runs-on` directive. The runner then:

1. **Receives the job**: The runner receives the set of instructions (steps) defined in the workflow.
2. **Executes the job**: It executes each step (e.g., shell commands or GitHub Actions) in the order defined in the workflow.
3. **Reports back**: After the job finishes (either successfully or with errors), the runner reports the status back to GitHub.

#### Example of Specifying a Runner in GitHub Actions

In GitHub Actions, you use the `runs-on` keyword to specify which runner will execute the job:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out code
        uses: actions/checkout@v2
      - name: Build the project
        run: make build
```

In this example, the workflow will be executed on a **GitHub-hosted runner** running `ubuntu-latest`.

#### Using Self-Hosted Runners

If you want to use your own machine as a runner, you can register it as a **self-hosted runner**:

```yaml
jobs:
  build:
    runs-on: self-hosted
    steps:
      - name: Run on self-hosted runner
        run: echo "Running on my own server"
```

Self-hosted runners are useful for custom environments, more powerful machines, or specific infrastructure needs.

---

### GitLab Runners

#### What is a GitLab Runner?

A **GitLab runner** is an application that works with GitLab CI/CD to run the jobs defined in your `.gitlab-ci.yml` file. Like GitHub, GitLab offers both **shared runners** (GitLab-hosted) and **specific runners** (self-hosted).

- **Shared runners**: These are hosted by GitLab and can be used by all GitLab projects.
- **Specific runners**: These are self-hosted and can be customized based on your project needs.

#### How Do GitLab Runners Work?

In GitLab CI/CD, the runner is responsible for executing jobs in the stages of a pipeline. The process works as follows:

1. **Pipeline Triggered**: When a pipeline is triggered (e.g., by a commit or a merge request), GitLab sends the jobs to available runners.
2. **Job Execution**: The runner pulls the job and starts executing the defined script in the `.gitlab-ci.yml` file.
3. **Job Reporting**: After execution, the runner sends the job results (pass, fail, or any errors) back to GitLab.

#### Example of Specifying a Runner in GitLab CI/CD

In GitLab, you can use **tags** to target specific runners. Runners with matching tags will pick up and execute the job.

```yaml
stages:
  - build
  - test

build_job:
  stage: build
  tags:
    - linux
    - docker
  script:
    - echo "Building the project"

test_job:
  stage: test
  script:
    - echo "Running tests"
```

In this example, the `build_job` will run on a runner with the `linux` and `docker` tags.

#### Using Self-Hosted Runners in GitLab

You can also set up your own runner in GitLab by installing the **GitLab Runner** application on your server. Once registered, you can use it in your `.gitlab-ci.yml` file by specifying the appropriate tags.

---

### Comparison: GitHub Actions Runners vs. GitLab Runners

| Feature               | GitHub Actions Runners        | GitLab Runners                 |
|-----------------------|-------------------------------|---------------------------------|
| **Hosted Runners**     | GitHub-hosted VMs for Ubuntu, macOS, Windows | GitLab shared runners for Linux |
| **Self-Hosted Runners**| Supported                     | Supported                       |
| **Targeting Runners**  | `runs-on` for GitHub-hosted or `self-hosted` | `tags` to match runners |
| **Customization**      | Custom machine setup with self-hosted runners | Custom environments with self-hosted runners |
| **Control**            | Limited on GitHub-hosted; full control with self-hosted | Full control with self-hosted runners |

---

### Conclusion

Runners are the backbone of CI/CD workflows and pipelines in both GitHub and GitLab. They execute the tasks defined in your YAML configuration, running on either shared, hosted infrastructure, or custom self-hosted machines. By understanding how to configure and use runners effectively, you can optimize your CI/CD processes to better suit your project's needs.
