### Minimal Automation Script

{% if page %}An minimal exemplary <i class="fab fa-github"></i> Workflow file could look like this:{% endif %}

```yaml
# .github/workflows/hello_world.yml

on:
  push:
    branches:
      - main

jobs:
  say_hello:
    steps:
      - uses: actions/checkout@v2
      - run: echo "Hello, World!"
```
