# oak9 GitHub Action

Use the oak9 GitHub action to scan for infrastructure-as-code errors in your oak9 action pipeline. By utilizing this
GitHub action in your project workflow, you can automatically start to find, fix and monitor your project for
configuration errors in Terraform.

## Highlighted Features

Using this Action provides the following features:
* App Security Design
* Infrastructure-as-Code Security Checks
* Automated Security Design Integration
* Security Design Enforcement
* Security Design Change Management
* Out of the box compliance regulations including: PCI DSS, ISO 27001, GDPR, CCPA HIPAA, HI TECH, State Regulations, NIS SP 800- 53

## Requirements

To run an analysis on your code, you first need to set up your project on [oak9](https://www.oak9.io/)

## Usage

The following is an example GitHub Actions workflow:

```yaml
name: Example workflow using oak9
on: push
jobs:
  oak9-iac-scan:
    runs-on: ubuntu-latest
    name: oak9-action
    steps:
    - name: Checkout repo
      uses: actions/checkout@v2
    - name: oak9 Github Action
      id: oak9
      uses: oak9io/oak9.githubaction@v1.0.2
      env:
        OAK9_API_TOKEN: ${{ secrets.OAK9_API_TOKEN }}
        GITHUB_REPOSITORY: $GITHUB_REPOSITORY
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        organizationId: '[your-oak9-organization-id]'
        projectId: '[your-oak9-project-id]'
        maximumSeverity: 'High'
        logDesignGaps: true
```

## Parameters

- `organizationId` - **_(Required)_** Your oak9 organization ID.
- `projectId` - **_(Required)_** Your oak9 project ID.
- `maximumSeverity` - **_(Required)_** The threshold at which a detected design gap will cause your workflow to fail. One of `none`, `low`, `moderate`, `high`, or `critical`.
- `logDesignGaps` - An indicator of whether you'd like any detected design gaps output to the GitHub Actions build log. Defaults to `false`.

## Secrets

- `OAK9_API_TOKEN` - **_(Required)_** This is the API token for your oak9 project.

## License

This project is released under the Apache 2.0 License.