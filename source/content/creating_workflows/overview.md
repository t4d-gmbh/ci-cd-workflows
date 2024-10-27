## <i class="fab fa-github"></i> Workflows vs. <i class="fab fa-gitlab"></i> Pipelines - Overview

| Feature                     | <i class="fab fa-github"></i> Workflows                          | <i class="fab fa-gitlab"></i>  Pipelines                          |
|-----------------------------|------------------------------------------------------------------|-------------------------------------------|
| **Location**                | Any `.yml` file in `.github/workflows/` | `.gitlab-ci.yml` in the root directory |
| **Mandatory Keys**          | <ul><li>`on`: determine when to be triggered</li><li> `jobs`: a set of jobs</li><li>`jobs.<job_name>.steps`: a list of tasks to run</li></ul>  | <ul><li>`<job_name>`: defining a job</li><li>`<job_name>.script`: list of shell commands</li></ul> |
| **Triggers**                | <ul><li>Uses top-level `on` key to trigger Workflow</li><li>Job-level `if` key to skip jobs</li></ul> | <ul><li>Uses `workflow.rules` key to trigger Pipeline</li><li>Job-level `rules` key to trigger jobs</li></ul> |
| **Variables**               | Defined in `env` at job or Workflow level | Defined in `variables` at job or Pipeline level |
| **Environment Variables**   | Provides "context variables" including `vars` and `secrets` defined via Web-UI | Provides predefined variables & custom variables defined via Web-UI |
