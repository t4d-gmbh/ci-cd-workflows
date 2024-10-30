## Types of Runners

:::{admonition} Instance Runners <i class="fab fa-gitlab"></i>
:class: note, margin
Self-hosted **GitLab** instances can provide their own "Remote Hosted Runners"{% if page %}, which are then be available to all Projects hosted on that instance.

_Read more about [Instance Runners](https://docs.gitlab.com/ee/ci/runners/runners_scope.html#instance-runners)_{% endif %}.
:::
{% if slide %}
:::{card} Remote Hosted Runners <i class="fab fa-gitlab"></i>&<i class="fab fa-github"></i>
Remote Hosted Runners are provided and maintained by the remote service.

A certain amount of runtime minutes or specific runner sizes may be offered free of charge.

These runners are ideal for automation scripts that **do not handle sensitive data**.

```{note}
Public Repositories can use lightweight runners on **GitHub** without any runtime restriction.
```
:::
:::{card} Self-Hosted Runners <i class="fab fa-gitlab"></i>&<i class="fab fa-github"></i>
Self-hosted runners are  virtual or physical machines **configured by the user** and registered with the remote service.

These runners can operate as a service and may be dedicated to specific <i class="fab fa-gitlab"></i> Projects or <i class="fab fa-github"></i> Repositories, or shared accross <i class="fab fa-github"></i> Organizations or <i class="fab fa-gitlab"></i> (Sub-)Groups.

They are suitable for **custom software and hardware requirements** or **specific security needs**.
:::
{% else %}

**Remote Hosted Runners**  
*Available: <i class="fab fa-gitlab"></i>, <i class="fab fa-github"></i>*  
Remote Hosted Runners are provided and maintained by the remote service, making them available to all users and projects. While some sizes or specific amounts of runtime may be offered free of charge, most remote services charge for the use of these runners.

These runners are readily availabe and ideal for automation procedures that **do not involve sensitive data**.

_Read more about remote hosted runners: [<i class="fab fa-gitlab"></i>](https://docs.gitlab.com/ee/ci/runners/index.html), [<i class="fab fa-github"></i>](https://docs.github.com/en/enterprise-cloud@latest/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners)_ 

---

**Self-Hosted Runners**  
*Available: <i class="fab fa-gitlab"></i>, <i class="fab fa-github"></i>*  
Self-hosted runners are **user-configured** virtual or physical machines that are registered with the remote service. They can be dedicated to specific GitLab Projects or GitHub Repositories, or shared across GitHub Organizations or GitLab (Sub-)Groups. These runners are well-suited for **custom software and hardware requirements** or **specific security needs**.

_Read more about self-hosted runners: [<i class="fab fa-gitlab"></i>](https://docs.gitlab.com/runner/#use-self-managed-runners), [<i class="fab fa-github"></i>](https://docs.github.com/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners)_  

---
{% endif %}
