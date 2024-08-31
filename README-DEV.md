# Development README

## CI/CD

This repository uses GitHub Actions for CI/CD. The CI/CD pipeline is defined in the `.github/workflows` directory. 

The CD pipeline is triggered by a repository_dispatch event, sent by the separate addon-repositories.

An UPDATER_TOKEN secret is used read-out the latest version of the addon-repositories. This token is a GitHub personal access token with the `repo` scope. 

The hassio-addons/repository-updater job is used to auto-generate README.md,  and update the addonsconfig.yaml and CHANGELOG.md to reflect the changes of the base repository.

## Testing this can be done locally using [ACT](https://github.com/nektos/act)

https://nektosact.com/usage/index.html

Act can be installed as en extension to the GitHub CLI.

Use the following command to test locally:

```
gh act -s UPDATER_TOKEN=<GITHUB_PAT> -W '.github/workflows/repository-updater.yaml' repository_dispatch
```













