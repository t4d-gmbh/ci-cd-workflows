### Start Small!

{% if page %}
CI/CD functionalities in **GitLab** and **GitHub** are excellent tools for speeding up, standardizing, and streamlining a variety of tasks.
However, adding complexity through pipelines or workflows can quickly increase the intricacy of your scripts.
Before you know it, you may find yourself navigating a maze of dependencies, conditions, and edge cases that can consume a significant amount of time to resolve and manage.

Therefore, before implementing any automation procedures, evaluate your workflow design and ensure it is as simple and straightforward as possible.
The fewer dependencies, the better!

Another important consideration is to avoid having multiple "sources of truth."
This concept may seem unusual at first, but adhering to the principle that any parameterization (such as the version of a dependency) should be defined in only one location—especially when used across multiple stages in a workflow or pipeline—can greatly simplify management.

Finally, even when starting small, it's essential to evaluate the structure of your project or repository before embarking on your automation journey.
The various features and configurations offered by remote services are designed to work well with standard project structures for languages like Python, R, Scala, etc.
Following typical project setups is likely to facilitate the use of automation functionalities, while maintaining custom folder structures and dependency patterns may lead to complications.

{% else %}
**Complex pipelines and workflows** can quickly increase the intricacy of your automation scripts.

- **Starting with simple, toy-like pipelines** allows you to experiment and learn without overwhelming complexity.
- **Simplicity in workflow design** is crucial; ensure it is as straightforward as possible.
    - **Fewer dependencies** lead to easier management and maintenance.
- **Avoiding multiple sources of truth** helps simplify management.
    - **Parameterization** (like dependency versions) should be defined in only one location, especially when used across multiple stages in a workflow or pipeline.
- **Evaluating project structure** before automation is essential.
    - **Standard project setups** for languages like Python, R, and Scala facilitate the use of automation functionalities, while custom structures may lead to complications.
{% endif %}

