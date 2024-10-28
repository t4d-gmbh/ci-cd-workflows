## Recap

{% if slide %}
- All you need is ...❤️? **A YAML file** 😉
- **Start small** with simple automation scripts.
- Define **when to trigger** an automation script.
- Use **remote hosted runners** when working with non-sensitive data.
- It is straight forward to **configure your own runner**.
- Configure you automation scripts to **use Docker containers**.
- Be aware of **security implications a runner has**.
- If at all, **store sensitive data in custom variables or the `secrets` context** via the Web-UI only!
{% else %}
Getting started with CI/CD is easier than it sounds—really, all you need is ❤️... well, a YAML file 😉.
Begin with small, simple automation scripts to familiarize yourself with CI/CD basics, such as automating tests or compiling code.
Setting clear trigger points for these scripts, like on code pushes or pull requests, will help manage when your workflows run.
For projects involving non-sensitive data, remote hosted runners are convenient and require minimal setup, while self-hosted runners offer more control and can be straightforward to configure.

To enhance reproducibility and flexibility, consider using Docker containers in your automation scripts, as they provide a consistent and isolated environment for your jobs, reducing the risk of environment-related issues.
As you gain confidence, don't hesitate to iterate on your automation scripts to improve efficiency and functionality.
However, always prioritize security; runners have access to your code and environment, making it essential to secure them properly.
Store sensitive data in custom variables or the secrets context via the Web UI to ensure your project remains protected.
{% endif %}
