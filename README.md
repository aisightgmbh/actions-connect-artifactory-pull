# Connect Artifactory Pull Action

[![Tests](https://github.com/aisightgmbh/actions-connect-artifactory-pull/actions/workflows/on_push.yaml/badge.svg)](https://github.com/aisightgmbh/actions-connect-artifactory-pull/actions/workflows/on_push.yaml)

This action can be used to create credentials to pull from AWS CodeArtifact.
The credentials are generated with the AWS CLI and put into the environment variables `POETRY_HTTP_BASIC_ARTIFACTORY_USERNAME` and `POETRY_HTTP_BASIC_ARTIFACTORY_PASSWORD`.
By default, the action will install the AWS CLI on the runner.
This behavior can be disabled by setting `install-aws`.

## Example

```yaml
jobs:
  example-job:
    runs-on: <YourCustomRunner>
    steps:
      - uses: actions/checkout@v3
      - uses: aisightgmbh/actions-connect-artifactory-pull@v1
        with:
          artifactory-owner: ${{ secrets.owner }}
          artifactory-domain: ${{ secrets.domain }}
          install-aws: true
      - run: echo $POETRY_HTTP_BASIC_ARTIFACTORY_PASSWORD
```
