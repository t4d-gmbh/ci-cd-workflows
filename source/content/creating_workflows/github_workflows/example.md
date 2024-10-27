### Example

{% if page %}An exemplary <i class="fab fa-github"></i> Workflow file could look like this:{% endif %}

```yaml
# .github/workflows/example.yml
name: CI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Run tests
        run: npm test
```
