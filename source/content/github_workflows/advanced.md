### Advanced Features

{% if slide %}- {% else %}:::{card}{% endif %} **`{%raw%}${{...}}{%endraw%}` Context Variables**{% if page %}:

As the name suggests, context variables hold contextual information and vary significantly under different running conditions.

Some important contextual variables are:

- **`github`**: Provides metadata about the Workflow run, repository, and event that triggered the workflow.
- **`vars`**: Contains variables definded on Repository, Organization or Environment level.
- **`secrets`**: Names and values of available secrets.

Refer to the official documentation for a [complete overview of **GitHub**'s contextual variables](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs) and [their availabilities](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/accessing-contextual-information-about-workflow-runs#context-availability).

:::{admonition} Inspect context variables
:class: tip

{% raw %}
```yaml
jobs:
  list-github-context:
    runs-on: ubuntu-latest
    steps:
      - name: Print GitHub Context Variables
        env:
          GITHUB_CONTEXT: ${{ toJSON(github) }}
        run: |
          echo "GitHub context variables:"
          echo "$GITHUB_CONTEXT" | jq '.'
```
{% endraw %}
:::
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Expression Evaluation**{% if page %}:

**GitHub** allows to [evaluate expressions](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/evaluate-expressions-in-workflows-and-actions) in the {%raw%}`${{...}}`{%endraw%} syntax.

{% raw %}
```yaml
jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - name: Set a message based on event type
        run: |
          MESSAGE="${{ github.event_name == 'push' && 'This is a push event!' || 'This is not a push event.' }}"
          echo $MESSAGE
```
{% endraw %}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using Workflow Templates**{% if page %}:

- **GitHub offers [pre-built workflow templates](https://docs.github.com/en/actions/writing-workflows/using-workflow-templates)** that can be used as-is or customized to meet your project needs.
- These templates simplify common tasks such as:
  - Testing code on different platforms or environments.
  - Deploying applications to various hosting services.
  - Scanning for security vulnerabilities or code quality issues.
:::{% endif %}


{% if slide %}- {% else %}:::{card}{% endif %} **Storing Secrets**{% if page %}:

Use **GitHub Secrets** to securely store sensitive information, like API keys or credentials. Secrets are encrypted and only available at runtime.

{% raw %}
  ```yaml
  jobs:
    deploy:
      runs-on: ubuntu-latest
      steps:
        - name: Deploy to production
          run: ssh -i ${{ secrets.SSH_PRIVATE_KEY }} user@server.com 'bash deploy.sh'
  ```
{% endraw %}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Creating Dependent Jobs**{% if page %}:

You can define job dependencies using the `needs` keyword, ensuring that jobs run in sequence.

{% raw %}
  ```yaml
  jobs:
    build:
      runs-on: ubuntu-latest
      steps:
        - run: echo "Building project"

    test:
      runs-on: ubuntu-latest
      needs: build
      steps:
        - run: echo "Running tests"

    deploy:
      runs-on: ubuntu-latest
      needs: test
      steps:
        - run: echo "Deploying to production"
  ```
{% endraw %}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using a Matrix**{% if page %}:

You can run a job multiple times with different configurations (e.g., testing across different versions of a programming language).

{% raw %}
  ```yaml
  jobs:
    test:
      runs-on: ubuntu-latest
      strategy:
        matrix:
          python-version: [3.7, 3.8, 3.9]
      steps:
        - name: Set up Python
          uses: actions/setup-python@v2
          with:
            python-version: ${{ matrix.python-version }}
        - run: python --version
  ```
{% endraw %}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Caching Dependencies**{% if page %}:

Speed up workflows by caching dependencies or files that are used across runs.

{% raw %}
  ```yaml
  jobs:
    build:
      runs-on: ubuntu-latest
      steps:
        - name: Cache node modules
          uses: actions/cache@v3
          with:
            path: node_modules
            key: ${{ runner.os }}-node-${{ hashFiles('package-lock.json') }}
  ```
{% endraw %}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using Databases and Service Containers**{% if page %}:

If your workflow requires a service like a database, you can define service containers that will run alongside the job.

{% raw %}
  ```yaml
  jobs:
    test:
      runs-on: ubuntu-latest
      services:
        postgres:
          image: postgres:12
          ports:
            - 5432:5432
          options: >-
            --health-cmd "pg_isready"
            --health-interval 10s
            --health-timeout 5s
            --health-retries 5
      steps:
        - run: psql --version
  ```
{% endraw %}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using Labels (Targeting Runners)**{% if page %}:

You can specify which runners to use for a job based on the runner's labels (e.g., `self-hosted`, `ubuntu-latest`).
{%raw%}
  ```yaml
  jobs:
    build:
      runs-on: self-hosted
      steps:
        - run: echo "Building project on a self-hosted runner"
  ```
{%endraw%}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Reusing Workflows**{% if page %}:

Use reusable workflows to call another workflow from within a workflow, reducing duplication of common tasks.
{% raw %}
  ```yaml
  jobs:
    call-another-workflow:
      uses: ./.github/workflows/reusable-workflow.yml
      with:
        param1: value1
  ```
{% endraw %}
:::{% endif %}

{% if slide %}- {% else %}:::{card}{% endif %} **Using Environments**{% if page %}:

You can define **environments** with specific secrets and protection rules for different stages of deployment (e.g., `development`, `staging`, `production`).
{% raw %}
  ```yaml
  jobs:
    deploy:
      runs-on: ubuntu-latest
      environment:
        name: production
        url: https://my-app.com
      steps:
        - run: echo "Deploying to production"
  ```
{% endraw %}
:::{% endif %}
