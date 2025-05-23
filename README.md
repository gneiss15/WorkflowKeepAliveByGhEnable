# Workflow keep alive by Gh Enable
GitHub Action to prevent GitHub from [disabling scheduled workflows due to 
repository inactivity][1].

[1]: https://docs.github.com/en/actions/learn-github-actions/usage-limits-billing-and-administration#disabling-and-enabling-workflows


This Action send a **__gh api -X PUT "repos/.../enable"__** for every workflow of the repository.

## Usage:

Create a workflow similar to:

```yaml
name: Test keep alive by Gh Enable
on:
  workflow_dispatch:
  push:
  schedule:
    - cron: '0 0 1 * *' # Use a schedule that runs at least every 59 Days
jobs:
  workflow-keepalive:
    runs-on: ubuntu-latest
    permissions:
      actions: write
    steps:
    - name: keepalive
      uses: gneiss15/WorkflowKeepAliveByGhEnable@v1
```

