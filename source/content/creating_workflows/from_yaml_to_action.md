## From YAML to Automation

{% if page %}
Both **GitHub** and **GitLab** use YAML files as blueprints for automated workflows.
However, it may be unclear how the content in these YAML blueprints is transformed into executable instructions and where these instructions actually run.

In the [<i class="fas fa-person-running "></i> Runners <i class="fas fa-person-running fa-flip-horizontal"></i>](../runners/index.md) section, we’ll focus on the execution environments.
Here, we provide a high-level overview of how remote services convert YAML configurations into actionable steps.
{% else %}
How is a YAML file turned into an automated workflow?
{% endif %}

1. **Syntax Parsing**: The remote service first checks the YAML syntax{% if page %} for any format errors to ensure the file can be processed{% endif %}.

2. **Parsing and Validating Structure**: {% if slide %}The remote service checks for required keys, and/or structured values.{% else %}Once syntax is confirmed, the remote service parses the YAML file, interpreting the structure based on service-specific expectations (like [GitHub Workflow](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions) or [GitLab Pipeline](https://docs.gitlab.com/ee/ci/yaml/) requirements).
   This involves identifying valid keys (such as `jobs` or `script`) and recognizing any errors in structure based on the remote service’s schema, not the YAML format itself.{% endif %}

3. **Generating Execution Instructions**: {% if slide %}The YAML file is translated into an ordered queue of jobs.{% else %}After parsing, the remote service generates a list of jobs, interprets dependencies, and builds an ordered queue of sets of jobs according to the specified order, triggers, and conditions.{% endif %}

4. **Runner Polling for Jobs**: {% if slide %}Runners periodically fetch jobs from the remote service{% else %}Runners are configured to periodically connect to the remote service to check if they qualify for any jobs awaiting execution.
   When a runner polls, the remote service assigns available jobs based on the runner’s configuration and labels.
   The runner then downloads the necessary scripts and artifacts and starts executing the assigned job in its environment.{% endif %}

5. **Running on Runners**: {% if slide %}The runner carries out the instructions in a job in the specified environment{% else %}Each job typically contains information about the environment in which it should run and a set of instructions to perform.
   The runner first sets up the environment and then executes the commands or actions.{% endif %}

6. **Job Completion and Result Reporting**: {% if slide %}The runner sends back a status report to the remote service.{% else %}Upon completion of the job, the runner sends a status report back to the remote service, indicating whether the job succeeded, failed, or was canceled.
   This report updates the job’s status on the CI/CD dashboard.{% endif %}

7. **Artifact and Log Collection**: {% if slide %}The runner uploads any artifacts and logs.{% else %}The runner uploads any artifacts (e.g., compiled binaries, test results) and logs generated during execution to the remote service.
   These files are stored with the job record, making them accessible for review, debugging, or downstream jobs.{% endif %}

8. **Pipeline Status Update and Notifications**: {% if slide %}The remote service aggregates job outcomes and propagates the status.{% else %}The remote service aggregates job statuses to update the overall pipeline status.
   If configured, notifications are sent to relevant team members via email, messaging platforms, or through the remote service’s UI.{% endif %}

9. **Retention and Cleanup**: {% if slide %}The remote service cleans up artifacts and logs periodically.{% else %}Artifacts and logs are retained according to the configured retention policy. After the retention period, the service automatically deletes these files to save storage space.{% endif %}
