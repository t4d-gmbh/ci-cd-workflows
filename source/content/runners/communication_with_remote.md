## Communication with Remote Service
{% if slide %}
**Communication Protocol**: Runners use **HTTP/HTTPS** to interact with remote services.

**Access Tokens**:
- Provided as predefined variables by **GitHub** and **GitLab**.
- Required for fetching protected resources.

**Runner Capabilities**:
- Can edit projects and repositories.
- Interact with features like Issues and Merge/Pull Requests.

**Communication Mode**:
- Runners initiate communication via **polling**.

**Network Accessibility**:
- Outgoing connections are necessary.
- Runners can operate in a semi-isolated environment (i.e. not reachable from WWW)
{% else %}
Runners communicate via HTTP/HTTPS with the remote service and might require access tokens to fetch protected ressources.
Both **GitHub** and **GitLab** provide tokens (e.g. the [<i class="fab fa-gitlab"></i> `CI_JOB_TOKEN`](https://docs.gitlab.com/ee/ci/jobs/ci_job_token.html) or the [<i class="fab fa-github"></i> `github.token`](https://docs.github.com/en/actions/security-for-github-actions/security-guides/automatic-token-authentication)) in the form of predefined variables that are available to the runner.

With those tokens the runner can be set up to perform edits in a <i class="fab fa-gitlab"></i> Project or <i class="fab fa-github"></i> Repository, be it in the actual <i class="fab fa-git"></i> repository or in assoicated features of the remote service, such as Issues, or Merge/Pull Requests.

One important aspect of the runner's communication with remote services is the mode with which communication is established.
Both for **GitLab** and **GitHub** runners, it is the runner instance that initiates the communication with the remote service by [polling](https://en.wikipedia.org/wiki/Polling_(computer_science)).
This has important consequences on network accessibility of a runner: While it needs outgoing connections to be possible, a runner does not need to be reachable from the internet and thus can reside in a semi-isolated environment.
{% endif %}
