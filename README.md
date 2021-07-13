# tflint-config
Scoop's default tflint configuration. 

## Usage

This configuration can be loaded from remote repositories and used to lint Terraform code.

```yaml
name: Terraform Lint
on:
  - push
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - id: fetch-tflint-config
        uses: ryanwholey/remote-tflint-config@v1
        with:
          source-repo: TakeScoop/tflint-config
      - uses: terraform-linters/setup-tflint@v1
        name: Setup TFLint
        with:
          tflint_version: v0.29.0
      - run: |
          tflint \
            --format compact \
            --config ${{ steps.fetch-tflint-config.outputs.config-path }}
```
