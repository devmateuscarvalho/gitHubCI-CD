# GitHub Actions CI Test

This repository is a demonstration of setting up a simple Continuous Integration (CI) workflow using GitHub Actions. The workflow is configured to print "Hello, World!" whenever a push is made to the repository.

## Workflow Configuration

The CI workflow is defined in a YAML file located at `.github/workflows/hello-world.yml`. The configuration is as follows:

```yaml
name: Hello World CI

on: [push]

jobs:
  say-hello:
    runs-on: ubuntu-latest

    steps:
      - name: Say Hello
        run: echo "Hello, World!"
