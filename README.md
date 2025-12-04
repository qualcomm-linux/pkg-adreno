# pkg-template

This repository serves as a template for creating Debian package repositories within the Qualcomm Linux ecosystem. It provides the essential structure, GitHub workflows, and configuration necessary to integrate with the [qcom-build-utils](https://github.com/qualcomm-linux/qcom-build-utils) repository, enabling standardized Debian package building processes.

For a comprehensive tutorial on utilizing this template with an example project, refer to the [pkg-example README](https://github.com/qualcomm-linux/pkg-example/blob/main/README.md).

## Quick Start

To create a new Debian package repository using this template:

1. Navigate to this repository's GitHub page and click the **"Use this template"** button located in the top right corner.
2. Name the new repository with the prefix `pkg-` to adhere to the naming convention for package repositories.
3. Ensure the **"Include all branches"** option is enabled. This action will initialize the repository with the required branch: `debian/latest`, which contains workflow files in the `.github/` directory.

## Branches

- **main**: The primary branch containing workflow logic in the `.github/` folder, along with boilerplate documentation files such as license, contribution guidelines, and this README.
- **debian/latest**: An orphan branch initialized during templating. It will hold a copy of the upstream source code integrated with Debian packaging metadata in the `debian/` folder.

## Workflows

The `main` branch includes the following workflows in the `.github/workflows/` directory:

- **qcom-preflight-checks.yml**: A sanity check workflow inherited from the base Qualcomm template.
- **stale-issues.yml**: A workflow for managing stale issues, also inherited from the base template.
- **build-debian-package.yml**: Builds the Debian package for this repository. This workflow serves as an entry point that invokes reusable workflows from the centralized qcom-build-utils repository.
- **promote-upstream.yml**: Promotes the package's tracking version to a new upstream release. This workflow also triggers reusable workflows in qcom-build-utils.

## Repository Configuration

### Repository Variables

Set the following repository variables to establish links between upstream and package repositories:

- **UPSTREAM_REPO_GITHUB_NAME**: The GitHub name of the upstream repository (e.g., `qualcomm-linux/qcom-example-package-source`).
- **PKG_REPO_GITHUB_NAME**: The GitHub name of the package repository (e.g., `qualcomm-linux/pkg-example`).

### Branch Protection Rules

Configure branch protection for `debian/latest`:

- Restrict deletions.
- Require pull requests before merging.
- Block force pushes.
- Add `build / build-debian-package` as a required status check.

### Additional Settings

- Enable **"Automatically delete head branches"** for pull requests.
- Allow only merge commits for pull request merges.
- Enable **release immutability** in the upstream repository.
- Add `qcom-service-bot` as a contributor with write access to the new repository.

### AWS Runners

For teams utilizing AWS runners, document the process for setting up and managing these resources as part of the repository configuration.

## Development

Refer to the [CONTRIBUTING.md](CONTRIBUTING.md) file for guidelines on contributing to this project.

## Getting in Contact

For support or inquiries, contact sbeaudoi@qti.qualcomm.com.

## License

pkg-template is licensed under the [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html). See [LICENSE.txt](LICENSE.txt) for the full license text.
