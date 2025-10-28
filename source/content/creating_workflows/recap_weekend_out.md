## Recap: Weekend Out Exercise

{% if page %}
Let's revisit last week's [**Weekend Out**](https://github.com/t4d-gmbh/Weekend-Out) exercise to deepen our understanding of <i class="fab fa-github"></i> **GitHub** workflows in practice.

{% endif %}

### What Actually Happened?

Think back to the exercise where multiple people (you, Alice, Bob, and Carol) were collaborating on a packing list. 
Some unexpected things happened automatically - let's understand why!

::::{grid} 1 1 2 2
:gutter: 3

:::{grid-item-card} {octicon}`question;1em` Key Questions
:class-header: sd-bg-warning sd-text-white

- What exactly was going on in the Weekend-Out repository?
- How did a merge conflict occur **automatically**?
- What triggered the workflows?
- Who (or what) made commits as "Carol[bot]" and "Alice[bot]"?
- Why did two drone lists end up in the main branch?

:::

:::{grid-item-card} {octicon}`light-bulb;1em` Hint
:class-header: sd-bg-info sd-text-white

Take another look at the `.github/workflows/` directory in the Weekend-Out repository.

Three workflow files were silently working in the background:
- `auto-commit-blanket.yml`
- `carols_drone_and_alice.yml`
- `carols_issue.yml`

:::

::::

{% if page %}
---

::: {admonition} Workflow 1: Auto-Commit Blanket
:class: tip, dropdown

```yaml
name: Auto Commit Blanket
on:
  create

jobs:
  auto-commit-on-blanket-branch:
    if: {% raw %}${{ contains(github.ref, 'essentials')}}{% endraw %}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
        with:
          ref: main
      - name: Make changes to packing_list.md
        run: |
          echo "- [ ] extrawarm blanket" >> packing_list.md
          git config --global user.name 'Carol[bot]'
          git config --global user.email 'Carol[bot]@wonderland.com'
          git add packing_list.md
          git commit -m "Adding warm blanket"
          git push origin main
```

**Questions:**
- What triggers this workflow? {octicon}`arrow-right;0.8em` The `create` event (when a branch is created)
- What's the condition? {octicon}`arrow-right;0.8em` Only runs if branch name contains 'essentials'
- What does it do? {octicon}`arrow-right;0.8em` Commits directly to `main` (not the feature branch!)
- **Why does this cause a conflict?** {octicon}`arrow-right;0.8em` You're editing the same line in two places


:::

:::{admonition} Workflow 2: Carol's Drone and Alice
:class: tip, dropdown


```yaml
name: Auto Commit Blanket
on:
  pull_request:
    types:
      - opened

jobs:
  adding-list:
    if: {% raw %}${{ contains(github.head_ref, 'restruct') }}{% endraw %}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
        with:
          ref: main
      - name: Adding drone to packing_list.md
        run: |
          echo "- [ ] drone" > Carols_drone_list.md
          echo "- [ ] extra battery" >> Carols_drone_list.md
          git config --global user.name 'Alice[bot]'
          git config --global user.email 'Alice[bot]@wonderland.com'
          git add Carols_drone_list.md
          git commit -m "Adding Carols drone list"
          git push origin main
```

**Questions:**
- What triggers this workflow? {octicon}`arrow-right;0.8em` Opening a pull request
- What's the condition? {octicon}`arrow-right;0.8em` PR branch name contains 'restruct'
- What does it do? {octicon}`arrow-right;0.8em` Creates `Carols_drone_list.md` and pushes to `main`
- **Why do two drone lists appear?** {octicon}`arrow-right;0.8em` Alice[bot] commits while you're working on your PR

:::

:::{admonition} Workflow 3: Carol's Issue Comment
:class: tip, dropdown


```yaml
name: Carols Issue
on:
  issues:
    types:
      - opened

jobs:
  carols_issue:
    if: {% raw %}${{ contains(github.event.issue.title, 'restruct')}}{% endraw %}
    runs-on: ubuntu-latest
    steps:
      - name: Carol comments
        run: |
          echo -e "**Carol** wants to create a dedicated list..." > msg
          export msg=$(cat msg)
          gh issue comment {% raw %}${{ env.EVENT }}{% endraw %} --body "$msg" \
            --repo {% raw %}${{ env.OWNER }}/${{ env.REPO }}{% endraw %}
```

**Questions:**
- What triggers this workflow? {octicon}`arrow-right;0.8em` Opening an issue
- What's the condition? {octicon}`arrow-right;0.8em` Issue title contains 'restruct'
- What does it do? {octicon}`arrow-right;0.8em` Posts a comment as Carol[bot]
- **Purpose?** {octicon}`arrow-right;0.8em` Simulates team collaboration and provides instructions

:::

### Understanding the Chaos

::::{grid} 1 1 2 2
:gutter: 3

:::{grid-item-card} {octicon}`git-merge;1em` The Merge Conflict
:class-header: sd-bg-danger sd-text-white

1. You create `feature/essentials` branch
2. **Workflow 1** immediately commits to `main` (adds "extrawarm blanket")
3. You locally add blankets to the feature branch
4. When you merge: **conflict!** (same line modified in both places)

:::

:::{grid-item-card} {octicon}`git-pull-request;1em` The Duplicate Lists
:class-header: sd-bg-danger sd-text-white

1. You create an issue with 'restruct' in title
2. You create a PR from a branch with 'restruct' in name
3. **Workflow 2** triggers and commits `Carols_drone_list.md` to `main`
4. You also create a drone list and merge your PR
5. **Result:** Two drone lists in `main`!

:::

::::

---

### Key Takeaways

::::{grid} 1 1 1 1
:gutter: 3

:::{grid-item-card} {octicon}`workflow;1em` Workflows Run Independently
:class-header: sd-bg-primary sd-text-white

Workflows are triggered by events, not by human intention. They run automatically and can make changes to your repository without your direct involvement.

:::

:::{grid-item-card} {octicon}`git-branch;1em` Branch Protection Matters
:class-header: sd-bg-primary sd-text-white

Allowing direct commits to `main` (as these workflows do) can lead to conflicts and unexpected state. Branch protection rules help prevent this.

:::

:::{grid-item-card} {octicon}`sync;1em` Always Pull Before Push
:class-header: sd-bg-primary sd-text-white

The workflows committed to `main` while you were working. Always pull the latest changes before merging to avoid conflicts.

:::

:::{grid-item-card} {octicon}`people;1em` Coordination is Critical
:class-header: sd-bg-primary sd-text-white

In a real team, workflows should be documented and coordinated. The "chaos" was intentional for learning, but in production, workflows should be predictable.

:::

::::

---

### Reflection Questions

Before we move on to <i class="fab fa-gitlab"></i> **GitLab** pipelines, consider:

1. **Event-Driven Architecture:** How do the `on:` triggers demonstrate event-driven automation?

2. **Conditional Execution:** How do the `if:` conditions control when jobs run?

3. **Context Access:** How do workflows access repository information ({% raw %}`github.ref`, `github.head_ref`, `github.event`{% endraw %})?

4. **Permissions:** What permissions did these workflows need and why?

5. **Bot Commits:** How did the workflows impersonate users (Carol[bot], Alice[bot])?

6. **Real-World Application:** How would you use similar patterns (without the chaos) in a real project?

{% endif %}
