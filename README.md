# tfsec-sarif-action

## Description

This Github Action will run the tfsec sarif check then add the report to the repo for upload.

Example usage

```yaml
name: tfsec
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  tfsec:
    name: tfsec sarif report
    runs-on: ubuntu-latest

    steps:
      - name: Clone repo
        uses: actions/checkout@master

      - name: tfsec
        uses: JaSiLez/tfsec-sarif-action@pgx
        with:
          sarif_file: tfsec.sarif         

      - name: Upload SARIF file
        uses: github/codeql-action/upload-sarif@v1
        with:
          # Path to SARIF file relative to the root of the repository
          sarif_file: tfsec.sarif         
```

### Inspired [here](https://github.com/aquasecurity/tfsec-sarif-action)
