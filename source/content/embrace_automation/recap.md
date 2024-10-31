## Recap

{% if slide %}
- All you need is ...❤️? **A YAML file!** 😉
- **Start small** with simple automation scripts.
- Define **trigger conditions** for your automation script.
- Use **remote hosted runners** for non-sensitive data.
- Easily **configure your own runner** to suit your needs.
- Set up your automation scripts to leverage **Docker containers**.
- Be mindful of the **security implications** associated with runners.
- If necessary, **only store sensitive data in custom variables or the `secrets` context** via the Web-UI only!
{% else %}

Getting started with CI/CD is easier than it sounds—really, all you need is ❤️... - well, a YAML file 😉.
Begin with small, simple automation scripts to familiarize yourself with CI/CD fundamentals, such as automating tests or compiling code.
Setting clear trigger points for these scripts, such as on code pushes or pull requests, will help manage when your workflows run.

For projects involving non-sensitive data, remote hosted runners are convenient and require minimal setup, while self-hosted runners offer more control and can be eady to configure.

To enhance reproducibility and flexibility, consider using Docker containers in your automation scripts. They provide a consistent and isolated environment for your jobs, reducing the risk of environment-related issues.
As you gain confidence, feel free to iterate on your automation scripts to improve efficiency and functionality.

However, always prioritize security. Runners have access to your code and environment, making it essential to secure them properly.
Store sensitive data only in custom variables or the secrets context via the Web UI to ensure your project remains protected.
{% endif %}

:::{admonition} Playground Repository
Use a private repository to experiment with automation scripts and workflows. 
:::
:::{tip} 
Have a (private) template repository with a basic CI/CD setup ready to go for new projects.
:::
