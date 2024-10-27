## Types of Runners

:::{admonition} Instance Runners <i class="fab fa-gitlab"></i>
:class: note, margin
Self-hosted **GitLab** instances can provide their own "Remote Hosted Runners"{% if page %} that will then be available to all Projects hosted on that instance.

_Read more about [Instance Runners](https://docs.gitlab.com/ee/ci/runners/runners_scope.html#instance-runners)_{% endif %}.
:::
{% if slide %}
:::{card} Remote Hosted Runners <i class="fab fa-gitlab"></i>&<i class="fab fa-github"></i>
Provided and maintained runners available to all users and projects.

A certain amount of minutes or particular runner sizes might be free of charge.

Ideal for automation scripts that **do not work with sensitive data**.

```{note}
Public Repostiries can use lightweight runners on **GitHub** without any runtime restriction.
```
:::
:::{card} Self-Hosted Runners <i class="fab fa-gitlab"></i>&<i class="fab fa-github"></i>
   Self-hosted runners are virtual or physical machines **configured by the user** and registered at the remote service.

Self-hosted runners can be dedicated to <i class="fab fa-gitlab"></i> Projects or <i class="fab fa-github"></i> Repositories or shared accross <i class="fab fa-github"></i> Oranizations or <i class="fab fa-gitlab"></i> (Sub-)Groups.

Suitable for **custom software and hardware requirements** or **specific security needs**.
:::
{% else %}

**Remote Hosted Runners**  
*Available: <i class="fab fa-gitlab"></i>, <i class="fab fa-github"></i>*  
Provided and maintained runners are available to all users and projects in the remote service.
Some sizes or runners, or a certain amount of minutes of runtime might be free of charge but generally remote services charge for the usage of runners.

These runners are readyly availabe and ideal for automation procedures that **do not use sensitive data**.

_Read more about remote hosted runners: [<i class="fab fa-gitlab"></i>](https://docs.gitlab.com/ee/ci/runners/index.html), [<i class="fab fa-github"></i>](https://docs.github.com/en/enterprise-cloud@latest/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners)_ 

---

**Self-Hosted Runners**  
*Available: <i class="fab fa-gitlab"></i>, <i class="fab fa-github"></i>*  
Self-hosted runners are virtual or physical machines **configured by the user** and registered at the remote service. They can be dedicated to GitLab Projects or GitHub Repositories, or shared across GitHub Organizations or GitLab (Sub-)Groups. These runners are suitable for **custom software and hardware requirements** or **specific security needs**.

_Read more about self-hosted runners: [<i class="fab fa-gitlab"></i>](https://docs.gitlab.com/runner/#use-self-managed-runners), [<i class="fab fa-github"></i>](https://docs.github.com/en/enterprise-cloud@latest/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners)_  

---
{% endif %}
