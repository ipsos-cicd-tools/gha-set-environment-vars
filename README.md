# Custom Github Action Template

This repository serves as a template for creating custom Github Actions

## Setup Instructions

1. Create new repo in the **ipsos-cicd-tools** Github org using this repo as the template in the drop down option. 
    - Use the naming schema "gha-ACTION_NAME"

2. Replace the existing **action.yml** file in the root directory with your own code

3. Branch protection is enabled for `main` so any changes will need to be made via Pull Requests 

4. Swap out this README for your own that is relevant to the action. Have it provide a descrition of what the action does as well as an example of use.

```
steps:
    - name: Checkout
      uses: actions/checkout@v4


    - name: Release Action
      uses: "git::https://github.com/ipsos-cicd-tools/<repo name>?ref=<version number>"
      with:
        token: ${{ secrets.GITHUB_TOKEN }}
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
