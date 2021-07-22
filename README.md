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
        uses: terraform-linters/tflint-load-config-action@v0
        with:
          source-repo: TakeScoop/tflint-config
      - uses: terraform-linters/setup-tflint@v1
      - run: tflint --format compact
```
