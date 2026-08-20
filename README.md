# .github — Contoso organization template repository

This is the **special `.github` repository** for the organization. GitHub treats it as the place to
put org-wide defaults, and Challenge 23 uses it to share reusable pipeline elements.

Everything here is **deliberately empty**. Filling these folders IS Challenge 23.

```text
.github/
  workflows/
    reusable-node-ci-cd.yml       <- you write this (workflow_call)
    reusable-dotnet-ci-cd.yml     <- you write this
    reusable-security-scan.yml    <- you write this
actions/
  setup-node-project/action.yml   <- composite action
  dotnet-build-test/action.yml    <- composite action
  deploy-container-app/action.yml <- composite action
pipeline-templates/
  stages/                          <- Azure Pipelines stage templates
  jobs/                            <- job templates
  steps/                           <- step templates
```

## Why a separate repo

| Thing | Where it must live |
|---|---|
| Reusable workflow (`workflow_call`) | Any repo. Called as `org/repo/.github/workflows/x.yml@ref` |
| Composite action | Any repo, in a folder with `action.yml` |
| Org-wide issue/PR templates, profile README | **Only** the `.github` repo |
| Azure Pipelines templates | Any repo, referenced via a `repositories:` resource |

Exam point: GitHub shares by **repo reference + git ref**. Azure Pipelines shares by declaring a
`repositories:` resource and then `extends:` or `template:`. Know both syntaxes.
