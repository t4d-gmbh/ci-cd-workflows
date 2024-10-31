## Configuring Runners

{% if slide %}
Configuring self-hosted runners is a well-documented process, with comprehensive guides for **GitLab** and **GitHub**  

**Important Considerations**  
  1. **Set Up Runners with Controlled Execution Environments**  
     - Use a Docker Executor in **GitLab**.  
     - In **GitHub**, specify Docker containers in your jobs.

     Benefits: Improved **reproducibility and reduced interference between jobs**

  2. **Secure Your Runner Adequately**  
     - Control access to repositories and secrets.
     - Be cautious when granting access to sensitive data. 

  3. **Provide Sufficient Resources**  
     - Ensure adequate CPU, memory, and disk space.  
     - Monitor performance to prevent bottlenecks  .

  4. **Consider All Resources**  
     - Evaluate the resources required for your automated setups.
     - Self-hosted runners can run on personal devices (laptops, workstations).
{% else %}
The configuration process for self-hosted runners is well-documented for both **GitLab** and **GitHub**.
You can find the relevant documentation here: [**GitLab**](https://docs.gitlab.com/runner/configuration/advanced-configuration.html) and [**GitHub**](https://docs.github.com/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners).
The process is streamlined to facilitate easy setup.

Both remote services offer a wide range of configuration options, which should be reviewed when actively setting up a self-hosted runner. 

Here are some important considerations to keep in mind:

1. **Set Up Runners with Controlled Execution Environments**  
   In **GitHub**, each job can specify a Docker container using the `container` key.
   You can also [adapt some configurations](https://docs.github.com/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/customizing-the-containers-used-by-jobs) for self-hosted runners regarding the usage of this key.  

   For **GitLab**, you need to specify an [Executor](https://docs.gitlab.com/runner/executors/index.html) for a self-hosted runner.
   The easiest choice is the [Docker Executor](https://docs.gitlab.com/runner/executors/docker.html), which allows you to run jobs in an isolated Docker environment.

   Using isolated execution environments not only enhances the reproducibility of individual jobs, but also reduces the risk of interference between jobs from different projects or repositories.

:::{warning}
:class: margin
This is particularly important when allowing to run:
- [Pipelines on Merge Requests from forked Projects](https://docs.gitlab.com/ee/ci/pipelines/merge_request_pipelines.html#use-with-forked-projects)
- [Workflows on Pull Requests from forked Repositories](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/approving-workflow-runs-from-public-forks)
:::
2. **Secure Your Runner Adequately**  
   A self-hosted runner has access to the repositories and projects it operates for and will receive any custom variables or secrets defined on the remote service.
   If you configure a self-hosted runner to access sensitive data, be aware that anyone with access to the project or repository on the remote service could potentially use the automation script to instruct the runner to access, alter, or share that sensitive data. 

3. **Provide Enough Resources**  
   Ensure that your self-hosted runners have adequate resources (CPU, memory, disk space) to handle the expected workload.
   Monitor the performance and adjust the resources as necessary to prevent bottlenecks or failures during job execution.

4. **Consider All Resources**
   When contemplating a switch to an automated setup, such as the **GitLab** Pipeline or **GitHub** Workflow, consider the resources you might allocate for a self-hosted runner.
   A self-hosted runner does not have to be confined to a data center or hosted on AWS; your laptop or workstation can also effectively serve as a runner.
{% endif %}
