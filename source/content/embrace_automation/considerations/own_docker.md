### Create your own Docker images

{% if page %}
**GitLab** and **GitHub** do not just use Docker extensively in they automation procedures, they also allow to easily create and distribute your own Docker images.

In doing so, you will not just create isolated and reproducible environments for your project, but a custom Docker image will also drastically reduce the runtime of your automation scripts, as all installation and configuration of the environment can be carried out when creating the Docker image.

:::{tip}
Head over to [furrer-lab/r-containers](https://github.com/furrer-lab/r-containers) so see a full fledged example for this approach.
:::
_Read more about creating Docker images on [<i class="fab fa-gitlab"></i> ](https://docs.gitlab.com/ee/user/packages/container_registry/build_and_push_images.html) and [<i class="fab fa-github"></i> ](https://docs.github.com/en/actions/use-cases-and-examples/publishing-packages/publishing-docker-images)_

{% else %}
- **Docker images** are a great way to create isolated and reproducible environments for your project.
- **Custom Docker images** can drastically reduce the runtime of your automation scripts.
    - **All installation and configuration** of the environment can be carried out when creating the Docker image.
- **GitLab** and **GitHub** allow you to easily create and distribute your own Docker images.
:::{tip}
Check out [furrer-lab/r-containers](https://github.com/furrer-lab/r-containers) for a full-fledged example of this approach.
:::
{% endif %}