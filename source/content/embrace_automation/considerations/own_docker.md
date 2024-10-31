### Create your own Docker images

{% if page %}
Both **GitLab** and **GitHub** leverage Docker extensively in their automation processes, and they make it easy for you to do create and distribute your own Docker images.

By creating custom Docker images, you not only establish isolated and reproducible environments for your projects but also drastically reduce the runtime of your automation scripts. This is because all installation and configuration of the environment can be completed during the image creation process.

:::{tip}
For a comprehensive example of this approach, check out [furrer-lab/r-containers](https://github.com/furrer-lab/r-containers).
:::
_Read more about creating Docker images on [<i class="fab fa-gitlab"></i> ](https://docs.gitlab.com/ee/user/packages/container_registry/build_and_push_images.html) and [<i class="fab fa-github"></i> ](https://docs.github.com/en/actions/use-cases-and-examples/publishing-packages/publishing-docker-images)_

{% else %}
- **Docker images** are a great way to create isolated and reproducible environments for your projects.
- **Custom Docker images** can significantly reduce the runtime of your automation scripts.
    - **All installation and configuration** can be completed during the Docker image creation process.
- **GitLab** and **GitHub** provide straightforward tools for creating and distributing your own Docker images.
:::{tip}
For a full-fledged example of this approach, check out [furrer-lab/r-containers](https://github.com/furrer-lab/r-containers).
:::
{% endif %}
