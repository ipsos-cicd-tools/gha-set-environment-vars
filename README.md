# gha-set-environment-vars

Sets environment variables based on the Github repo branch.

Outputs:
* environment = "*[development]*"
* short_env = "*[dev]*"

## Example Use

```
jobs:
  prepare:
    name: Get Branch & set Env vars
    runs-on: ubuntu-latest
    outputs:
      environment: ${{ steps.set-environment-and-path.outputs.environment }}
      short_env: ${{ steps.set-environment-and-path.outputs.short_env }}
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - id: set-environment-and-path
        uses: "ipsos-cicd-tools/gha-set-environment-vars@1.0.0"
```



## Workflow Overview

The CI/CD workflow automates the following tasks:

All Branches
1. **Validate**: Runs `yamllint` against the action yaml file.

Main Branch only

2. **Release**: Creates a Github release using Semantic-Release
    - Be sure to begin the commit message with one of the following to ensure a new release version is generated: [ `BREAKING_CHANGE:`, `feat:`, `fix:`]


## Triggering the Workflow

The default workflow triggers on every push to any branch. The Create Release step will only run on pushes to `main`


## Feedback and Contributions

Feedback and contributions to this template are welcome. Please open an issue or pull request in this repository.


</br>

---

*This README is part of a template repository for automating Docker workflows with GitHub Actions and GCP Artifact Registry.*
