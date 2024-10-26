### Evaluation

{% if page %}
**GitHub** evaluates a workflow file (`.yml`) by interpreting the structure and content of the YAML file, including variables and environment settings during the workflow execution:
{% endif %}

{% if page %}####{% endif %} 1. **Parsing and Loading the Workflow File**
{% if page %}
- GitHub reads and parses the workflow file located in `.github/workflows/`.
- The file is structured in YAML and specifies events, jobs, and steps.
{% endif %}

{% if page %}####{% endif %} 2. **Triggering Events**
{% if page %}
- Workflows are triggered by specific events defined under the `on:` section (e.g., `push`, `pull_request`).
- Once an event occurs, the workflow begins, and variables like `github.*` and environment variables start being evaluated.
{% endif %}

{% if page %}####{% endif %} 3. **Evaluating Workflow Variables**
{% if slide %} {% endif %}   - **Predefined Variables**{% if page %}:
     These variables are scoped to the workflow and depend on the repository and event context:
     
     {% raw %}
     - **`${{ github }}`**: Provides metadata about the repository and the event.
       - `${{ github.repository }}`: Repository name (e.g., `user/repo`).
       - `${{ github.actor }}`: The username of the actor triggering the workflow.
       - `${{ github.ref }}`: The branch or tag ref triggering the workflow.
     {% endraw %}
       
     These variables are evaluated based on the repository and event state **at the time of the trigger**.
     
     {% raw %}
     ```yaml
     jobs:
       example-job:
         runs-on: ubuntu-latest
         steps:
           - name: Print repository name
             run: echo "Repository: ${{ github.repository }}"
     ```
     {% endraw %}
     {% endif %}
{% if slide %} {% endif %}   - **Environment Variables (`env`)**{% if page %}:
     
     {% raw %}
     - **`${{ env }}`**: User-defined environment variables set at the workflow, job, or step level. Referenced using `${{ env.VAR_NAME }}`.
     {% endraw %}
     - Evaluated during the job or step where they are used.
     
     {% raw %}
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
     {% endraw %}
     {% endif %}
  
{% if page %}####{% endif %} 4. **Evaluating Workflow Expressions**
   {% if page %}
   {% raw %}
   GitHub Actions allows logic with expressions inside `${{ }}`.
   
   - `${{ github.event_name == 'push' }}`: Evaluates if the event is a `push`.
   - `${{ runner.os }}`: Information about the runner’s OS.
   {% endraw %}
   
   Expressions are evaluated **just before a job or step runs**.
   
   {% raw %}
   ```yaml
   jobs:
     test:
       runs-on: ubuntu-latest
       if: ${{ github.event_name == 'push' }}
       steps:
         - name: Run tests
           run: ./run-tests.sh
   ```
   {% endraw %}
   {% endif %}

{% if page %}####{% endif %} 5. **Execution of Jobs and Steps**
{% if page %}
{% raw %}
- Jobs execute on GitHub-hosted or self-hosted runners.
- Variables and expressions like `${{ github.* }}` and `${{ secrets.* }}` are evaluated **just before each step**.
{% endraw %}

{% if page %}####{% endif %} 6. **Secrets and Secure <i class="fab fa-github"></i> Variables** Secrets (e.g., `secrets.GITHUB_TOKEN`, `secrets.MY_SECRET`) are evaluated **at runtime** and injected into the environment only during job or step execution.

{% raw %}
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
{% endraw %}
{% endif %}

{% if page %}####{% endif %} 7. **Evaluating On-the-Fly Variables**
{% if page %}
Variables generated as part of a workflow (e.g., step outputs) are evaluated once they are produced and can be referenced by other steps.

{% raw %}
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
{% endraw %}
{% endif %}

---

#### Key Points:
- **When are GitHub variables evaluated?**  
  Variables like `github.*` are evaluated **before each job starts** based on the event context.
  
- **When are environment variables evaluated?**  
  Environment variables (`env`) and step-specific outputs are evaluated **when a job or step starts running**.

In summary, GitHub evaluates a workflow file by parsing the structure, reacting to triggers, and evaluating variables and expressions at different stages of the workflow, ensuring dynamic values are injected at the appropriate time.
