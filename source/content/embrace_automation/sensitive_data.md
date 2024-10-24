## Self-Hosted Runner Accessing Secrets and Sensitive Data in a Protected Environment

### Overview
A self-hosted runner can be configured to securely access secrets and sensitive data while residing in a protected environment. This setup enhances security by limiting exposure to sensitive information and ensuring that the runner operates within a controlled network.

### Setup Components

#### 1. Protected Environment
- **Description**: A secure network or virtual environment (e.g., a private cloud, virtual private network (VPN), or isolated server) where the self-hosted runner operates.
- **Purpose**: To minimize exposure to external threats and ensure that sensitive data is only accessible within a controlled environment.

#### 2. Secrets Management Tool
- **Examples**: HashiCorp Vault, AWS Secrets Manager, Azure Key Vault.
- **Purpose**: Store and manage sensitive data such as API keys, passwords, and tokens securely.

#### 3. Self-Hosted Runner
- **Description**: A runner installed within the protected environment that executes CI/CD jobs.
- **Configuration**: Ensure the runner has the necessary permissions to access the secrets management tool and is configured to operate within the protected network.

#### 4. Environment Variables
- **Usage**: Configure the self-hosted runner to use environment variables to store access credentials for the secrets management tool.
- **Example**: 
  - `VAULT_ADDR` for HashiCorp Vault URL.
  - `VAULT_TOKEN` for authentication.

#### 5. CI/CD Pipeline Configuration
- **Trigger**: When a job is executed on the self-hosted runner.
- **Action**:
  - Use scripts or plugins to authenticate with the secrets management tool.
  - Retrieve the required secrets and store them in environment variables for the duration of the job.

#### 6. Access Control
- **Implementation**: 
  - Use role-based access control (RBAC) to limit which secrets the self-hosted runner can access.
  - Regularly audit access logs to ensure compliance and security.

### Example Workflow

1. **Job Execution**:
   - The self-hosted runner starts a CI/CD job within the protected environment.
   
2. **Authenticate**:
   - The runner authenticates with the secrets management tool using stored environment variables.

3. **Retrieve Secrets**:
   - The runner fetches the necessary secrets for the job (e.g., database credentials, API keys) from the secrets management tool, which is also accessible within the protected environment.

4. **Run Job**:
   - The job executes with the retrieved secrets, ensuring that sensitive data is not hard-coded in the codebase and remains within the secure environment.

5. **Cleanup**:
   - After the job completes, any temporary environment variables containing sensitive data are cleared.

:::{admonition} Note on Triggers for Merge/Pull Requests
:class: warning
When configuring CI/CD pipelines to trigger on merge or pull requests, be cautious about the exposure of sensitive data. If the feature branch contains untrusted code or if the pull request is from an external contributor, there is a risk that malicious code could access sensitive information during the CI/CD process. To mitigate this risk, consider implementing additional security measures, such as:
- Limiting access to secrets for jobs triggered by pull requests from untrusted sources.
- Using separate environments for testing pull requests that do not have access to production secrets.
- Conducting thorough code reviews and security checks before merging changes.
:::

### Summary
By integrating a self-hosted runner within a protected environment and using a secrets management tool, teams can securely access and manage sensitive data during CI/CD processes. This approach enhances security by limiting exposure to external threats and ensuring that sensitive information is only accessible within a controlled network.
