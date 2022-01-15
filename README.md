# automerge-labeler

GitHub action which labels pull requests with are scheduled to be auto-merged for better visibility in the pull request overview.

# Setup

Create a new workflow file (e.g. *automerge-labeler.yml*) with the following content:

```yml
# This workflow labels PRs for which automerge is enabled with a label so that we can easily spot them in the PR overview UI.

name: Label auto-merge PRs

on:
  pull_request:
    branches: [ main ] # target branch for your PRs
  pull_request_target:
    types: [ auto_merge_enabled, auto_merge_disabled ]
jobs:
  add_remove_labels:
    runs-on: ubuntu-latest
    steps:
      - uses: ubuntudroid/automerge-labeler@v1
        with:
          token: ${{secrets.GITHUB_TOKEN}} # optional
          label: 'auto-merge' # optional
```

# Honorable mentions

This action uses the awesome [add-remove-label action](buildsville/add-remove-label).