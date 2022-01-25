# github-actions

## [Issue to Jira When Labeled](.github/workflows/create-jira-issue.yaml)

Clone a GitHub issue in Jira when a specific label is added.

### Usage

Create a yaml file containing the following at `.github/workflows/create-jira-issue.yaml`

```yaml
on:
  issues:
    types: [labeled]

name: Create Jira Issue

jobs:
  create-jira-issue:
    uses: SmartThingsCommunity/github-actions/.github/workflows/create-jira-issue.yaml@main
    with:
      trigger-label: example
      project: EXAMPLE
      fields: '{"labels": ["ex-github"],"components": [{"id": "10000"}]}'
    secrets:
      JIRA_BASE_URL: ${{ secrets.JIRA_BASE_URL }}
      JIRA_USER_EMAIL: ${{ secrets.JIRA_USER_EMAIL }}
      JIRA_API_TOKEN: ${{ secrets.JIRA_API_TOKEN }}
```

The above would create a Jira issue under the "EXAMPLE" project when the `example` label is added to a GitHub issue.

#### Inputs

`trigger-label`: The GitHub label that will trigger the workflow when added to an issue.

For all other inputs/secrets/outputs above, see [Jira Login](https://github.com/atlassian/gajira-login) and [Jira Create](https://github.com/atlassian/gajira-create).
