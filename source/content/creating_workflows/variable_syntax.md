## Understanding Variable Syntax in YAML Files

{% raw %}
### Overview of `$` and `${{ ... }}` Syntax

In YAML files used for CI/CD workflows (like GitHub Actions and GitLab CI/CD), the `$` and `${{ ... }}` syntax is essential for referencing variables, secrets, and context information.

#### 1. The `$` Syntax

- **Purpose**: Used to reference environment variables and predefined variables.
- **Usage**:
  - Directly access environment variables.
  - Access predefined variables provided by the CI/CD platform.

##### Example in GitLab CI/CD:
```yaml
script:
  - echo "Current branch: $CI_COMMIT_BRANCH"
```

#### 2. The `${{ ... }}` Syntax

- **Purpose**: Used for expressions in GitHub Actions, allowing for dynamic evaluation of context and variables.
- **Usage**:
  - Access context information (e.g., event details, job status).
  - Evaluate expressions and perform conditional logic.

##### Example in GitHub Actions:
```yaml
steps:
  - name: Print event name
    run: echo "Event: ${{ github.event_name }}"
```

#### 3. Key Differences

- **Evaluation Context**:
  - `$` is evaluated in the context of the environment at runtime.
  - `${{ ... }}` is evaluated at the time the workflow is defined, allowing for more complex expressions.

### Conclusion

Understanding how to use `$` and `${{ ... }}` syntax in YAML files is crucial for effectively managing variables in CI/CD workflows. These syntaxes enable dynamic and context-aware automation, enhancing the flexibility and power of your pipelines.
{% endraw %}
