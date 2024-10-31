## Communication with Remote Service
{% if slide %}
**Communication Protocol**: Runners use **HTTP/HTTPS** to interact with remote services.

**Communication Mode**: Runners initiate communication via **polling**.

**Runner Capabilities**:
- Can edit <i class="fab fa-gitlab"></i>Projects/<i class="fab fa-github"></i>Repositories.
- Interact with features like Issues and Merge/Pull Requests.

**Access Tokens**:
- Provided as predefined variables by **GitHub** and **GitLab**.
- Required for fetching protected resources.

**Network Accessibility**:
- Outgoing connections are necessary.
- Runners can operate in a semi-isolated environment (i.e. not reachable from WWW)
{% else %}
Runners communicate with remote services via HTTP/HTTPS and may require access tokens to fetch protected ressources.
Both **GitHub** and **GitLab** provide tokens (e.g., the [<i class="fab fa-gitlab"></i> `CI_JOB_TOKEN`](https://docs.gitlab.com/ee/ci/jobs/ci_job_token.html) or the [<i class="fab fa-github"></i> `github.token`](https://docs.github.com/en/actions/security-for-github-actions/security-guides/automatic-token-authentication)) in the form of predefined variables that are available to the runner.

With these tokens, the runner can perform edits in a <i class="fab fa-gitlab"></i> Project or <i class="fab fa-github"></i> Repository, whether in the actual <i class="fab fa-git"></i> repository or in assoicated features of the remote service, such as Issues or Merge/Pull Requests.

An important aspect of the runner's communication with remote services is the mode with which communication is established.
For both **GitLab** and **GitHub**, the runner instance that initiates communication with the remote service by [polling](https://en.wikipedia.org/wiki/Polling_(computer_science)).
This has signifant implications for the network accessibility of a runner: while it requires outgoing connections, the runner does not need to be reachable from the internet, allowing it to reside in a semi-isolated environment.
{% endif %}
