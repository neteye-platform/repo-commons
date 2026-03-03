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

## Contributing

Changes to these configurations and workflows affect multiple repositories.
Please ensure that updates are thoroughly tested and reviewed to prevent issues
across dependent repositories.
