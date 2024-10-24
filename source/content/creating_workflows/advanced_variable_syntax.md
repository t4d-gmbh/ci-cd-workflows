## Advanced Variable Syntax in YAML

### Overview

{% raw %}
In addition to the basic `$` and `${{ ... }}` syntax, there are several advanced methods for inserting and managing variables in YAML files, particularly in CI/CD workflows like GitHub Actions and GitLab CI/CD.

#### 1. Environment Variables

- **Direct Definition**: Define environment variables at the job or step level.
  
  ```yaml
  jobs:
    example_job:
      runs-on: ubuntu-latest
      env:
        MY_VAR: "Hello, World!"
      steps:
        - name: Print variable
          run: echo "$MY_VAR"
  ```

#### 2. Matrix Builds

- **Matrix Strategy**: Use a matrix strategy to define multiple sets of variables for jobs.

  ```yaml
  jobs:
    build:
      runs-on: ubuntu-latest
      strategy:
        matrix:
          node-version: [10, 12, 14]
      steps:
        - name: Use Node.js
          run: echo "Node version: ${{ matrix.node-version }}"
  ```

#### 3. Default Values

- **Setting Defaults**: Use the `defaults` context to set default values for variables.

  ```yaml
  defaults:
    run:
      shell: bash
      env:
        DEFAULT_VAR: "Default Value"

  jobs:
    example_job:
      runs-on: ubuntu-latest
      steps:
        - name: Print default variable
          run: echo "$DEFAULT_VAR"
  ```

#### 4. Job Outputs

- **Passing Outputs**: Set outputs in one job and reference them in another.

  ```yaml
  jobs:
    build:
      runs-on: ubuntu-latest
      outputs:
        build_id: ${{ steps.build_step.outputs.build_id }}
      steps:
        - id: build_step
          run: echo "::set-output name=build_id::12345"

    deploy:
      runs-on: ubuntu-latest
      needs: build
      steps:
        - name: Use build ID
          run: echo "Build ID: ${{ needs.build.outputs.build_id }}"
  ```

#### 5. Conditional Expressions

- **Using Conditions**: Set variables based on specific conditions.

  ```yaml
  jobs:
    example_job:
      runs-on: ubuntu-latest
      steps:
        - name: Set variable conditionally
          run: |
            if [ "${{ github.event_name }}" == "push" ]; then
              echo "This is a push event."
            fi
  ```
{% endraw %}

### Conclusion

These advanced variable management techniques enhance the flexibility and dynamism of your CI/CD workflows, allowing for more context-aware automation processes.
