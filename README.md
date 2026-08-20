# Repo Commons

This repository serves as a central hub for shared configurations and reusable
files across the **neteye-platform** organization.
It helps maintain consistency, reduce duplication, and simplify the management
of common CI/CD tasks and tool configurations.

## Shared Configurations

### Renovate Bot

This repository provides a base Renovate configuration that other repositories
can extend.

To use the shared configuration, add the following to the `renovate.json` file
in your repository:

```json
{
  "extends": ["github>neteye-platform/repo-commons"]
}
```

## Reusable Workflows

The workflows in this repository are designed to be called by other repositories
using GitHub's `workflow_call` feature.

Every workflow is self-documented: how to call it, its inputs and the secrets
it requires are described in the comment at the top of the workflow file.

| Workflow                   | Purpose                                               | File                                                                                   |
| -------------------------- | ----------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Backport                   | Backport merged pull requests to maintenance branches | [`backport.yaml`](.github/workflows/backport.yaml)                                     |
| Build Docker Image         | Build and publish a Docker image                      | [`build-docker-image.yaml`](.github/workflows/build-docker-image.yaml)                 |
| CodeQL Scan                | Run CodeQL static security analysis                   | [`codeql-scan.yaml`](.github/workflows/codeql-scan.yaml)                               |
| Common Cron Checks         | Scheduled, recurring checks                           | [`common-cron-checks.yaml`](.github/workflows/common-cron-checks.yaml)                 |
| Common Manual Checks       | Checks triggered manually                             | [`common-manual-checks.yaml`](.github/workflows/common-manual-checks.yaml)             |
| Common Pull Request Checks | Checks run on pull requests                           | [`common-pull-request-checks.yaml`](.github/workflows/common-pull-request-checks.yaml) |
| Pre-commit Checks          | Run pre-commit hooks                                  | [`pre-commit-checks.yaml`](.github/workflows/pre-commit-checks.yaml)                   |
| Semgrep Scan               | Run Semgrep static analysis                           | [`semgrep-scan.yaml`](.github/workflows/semgrep-scan.yaml)                             |
| Stale Check                | Mark and close stale issues and pull requests         | [`stale-check.yaml`](.github/workflows/stale-check.yaml)                               |
| Template Sync              | Sync changes from a template repository               | [`template-sync.yaml`](.github/workflows/template-sync.yaml)                           |
| Trivy Scan                 | Scan container images for vulnerabilities             | [`trivy-scan.yaml`](.github/workflows/trivy-scan.yaml)                                 |
| Validate PR Title          | Validate pull request title conventions               | [`validate-pr-title.yaml`](.github/workflows/validate-pr-title.yaml)                   |

### GitHub App token

Workflows that act on the consuming repository (for example **Stale Check**)
can authenticate as the **NetEye Steward** GitHub App using the `NETEYE_APP_ID`
variable and the `NETEYE_APP_PRIVATE_KEY` secret.
Consuming repositories must define those (and install the app) for those
workflows to take action.

## Contributing

Changes to these configurations and workflows affect multiple repositories.
Please ensure that updates are thoroughly tested and reviewed to prevent issues
across dependent repositories.
