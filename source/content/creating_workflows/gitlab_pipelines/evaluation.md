### Evaluation

{% if page %}
**GitLab** evaluates a CI/CD configuration file (`.gitlab-ci.yml`) by interpreting the structure and content of the YAML file, including variables and environment settings during the pipeline execution:
{% endif %}

{% if page %}####{% endif %} 1. **Parsing and Loading the Configuration File**
{% if page %}
- GitLab reads and parses the configuration file located in the root of the repository.
- The file is structured in YAML and specifies stages, jobs, and scripts.
{% endif %}

{% if page %}####{% endif %} 2. **Triggering Events**
{% if page %}
- The Pipeline can be triggered [by various events](https://docs.gitlab.com/ee/ci/jobs/job_rules.html#ci_pipeline_source-predefined-variable) (e.g., `push`, `schedule`).
- Once an event occurs, the pipeline begins, and variables like `CI_*` and environment variables start being evaluated.
{% endif %}

{% if page %}####{% endif %} 3. **Evaluating Pipeline Variables**
{% if page %}
When exactly variables are evaluated depends on the variable and where it is defined.
Generally, **GitLab** know three evaluation levels:

- **GitLab Server**
- **Runner**
- **Execution Shell**

Refer to the official documentation to learn more about [when variables are evalueated](https://docs.gitlab.com/ee/ci/variables/where_variables_can_be_used.html#expansion-mechanisms).
{% endif %}
  
{% if page %}####{% endif %} 4. **Evaluating Pipeline Expressions**
   {% if page %}
   {% raw %}
   GitLab CI/CD allows logic with expressions inside `rules` and `only/except`.
   
   - `if: '$CI_COMMIT_BRANCH == "main"'`: Evaluates if the branch is `main`.
   - `when: on_success`: Specifies when to run a job based on the success of previous jobs.
   {% endraw %}
   
   Expressions are evaluated **just before a job runs**.
   
   {% raw %}
   ```yaml
   job_name:
     script:
       - echo "This job runs only on the main branch"
     rules:
       - if: '$CI_COMMIT_BRANCH == "main"'
   ```
   {% endraw %}
   {% endif %}

{% if page %}####{% endif %} 5. **Execution of Jobs**
{% if page %}
{% raw %}
- Jobs execute on GitLab runners, which can be shared or specific to your project.
- Some variables are evaluated **just before each job starts**.
{% endraw %}
{% endif %}

{% if page %}####{% endif %} 6. **Evaluating On-the-Fly Variables**
{% if page %}
Variables generated as part of a job (e.g., job artifacts) are evaluated once they are produced and can be referenced by subsequent jobs.

{% raw %}
```yaml
job1:
  script:
    - echo "result=success" >> job_output.txt
  artifacts:
    reports:
      dotenv: job_output.txt

job2:
  script:
    - echo "The result is $RESULT"
```
{% endraw %}
{% endif %}

