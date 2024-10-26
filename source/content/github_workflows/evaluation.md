### {octicon}`workflow` Workflow Evaluation

{% if page %}
GitHub evaluates a workflow file (`.yml`) by interpreting the structure and content of the YAML file, including variables and environment settings during the workflow execution:
{% endif %}

### 1. **Parsing and Loading the Workflow File**
- GitHub reads and parses the workflow file located in `.github/workflows/`.
- The file is structured in YAML and specifies events, jobs, and steps.

### 2. **Triggering Events**
- Workflows are triggered by specific events defined under the `on:` section (e.g., `push`, `pull_request`).
- Once an event occurs, the workflow begins, and variables like `github.*` and environment variables start being evaluated.

### 3. **Evaluating Workflow Variables**
#### **Predefined GitHub Variables** <i class="fa fa-github"></i>
These variables are scoped to the workflow and depend on the repository and event context:

{% raw %}
- **`${{ github }}`**: Provides metadata about the repository and the event.
  - `${{ github.repository }}`: Repository name (e.g., `user/repo`).
  - `${{ github.actor }}`: The username of the actor triggering the workflow.
  - `${{ github.ref }}`: The branch or tag ref triggering the workflow.
  
These variables are evaluated based on the repository and event state **at the time of the trigger**.

```yaml
jobs:
  example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Print repository name
        run: echo "Repository: ${{ github.repository }}"
```

:::{admonition} Inspect the `github` context variable
:class: tip
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
:::

#### **Environment Variables (`env`)**
- **`${{ env }}`**: User-defined environment variables set at the workflow, job, or step level. Referenced using `${{ env.VAR_NAME }}`.
- Evaluated during the job or step where they are used.

```yaml
env:
  MY_ENV_VAR: "Hello, world"

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Print environment variable
        run: echo ${{ env.MY_ENV_VAR }}
```

### 4. **Evaluating Workflow Expressions**
GitHub Actions allows logic with expressions inside `${{ }}`.

- `${{ github.event_name == 'push' }}`: Evaluates if the event is a `push`.
- `${{ runner.os }}`: Information about the runner’s OS.

Expressions are evaluated **just before a job or step runs**.

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    if: ${{ github.event_name == 'push' }}
    steps:
      - name: Run tests
        run: ./run-tests.sh
```

### 5. **Execution of Jobs and Steps**
- Jobs execute on GitHub-hosted or self-hosted runners.
- Variables and expressions like `${{ github.* }}` and `${{ secrets.* }}` are evaluated **just before each step**.

### 6. **Secrets and Secure Variables** <i class="fa fa-github"></i>
Secrets (e.g., `secrets.GITHUB_TOKEN`, `secrets.MY_SECRET`) are evaluated **at runtime** and injected into the environment only during job or step execution.

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to server
        run: ssh deploy@server.com
        env:
          DEPLOY_TOKEN: ${{ secrets.DEPLOY_TOKEN }}
```

### 7. **Evaluating On-the-Fly Variables**
Variables generated as part of a workflow (e.g., step outputs) are evaluated once they are produced and can be referenced by other steps.

```yaml
jobs:
  example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Generate an output
        id: step1
        run: echo "::set-output name=result::success"
      - name: Use the output
        run: echo "The result is ${{ steps.step1.outputs.result }}"
```

---

### Key Points:
- **When are GitHub variables evaluated?**  
  Variables like `github.*` are evaluated **before each job starts** based on the event context.
  
- **When are environment variables evaluated?**  
  Environment variables (`env`) and step-specific outputs are evaluated **when a job or step starts running**.

In summary, GitHub evaluates a workflow file by parsing the structure, reacting to triggers, and evaluating variables and expressions at different stages of the workflow, ensuring dynamic values are injected at the appropriate time.
{% endraw %}
