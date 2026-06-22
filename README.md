# pkg-qcom-adreno

This repository has debian packaging rules and scripts for [prebuilt qcom-adreno binaries](https://qartifactory-edge.qualcomm.com/ui/native/qsc_releases/software/chip/component/gfx-adreno.le.0.0).

## Branches

- **qli-ci**: The primary branch containing workflow logic in the `.github/` folder, along with boilerplate documentation files such as license, contribution guidelines, and this README.
- **qcom/ubuntu/resolute**: This branch contains qcom-adreno debian packaging rules and scripts for Ubuntu 26.04 (Resolute Raccoon).
- **qcom/debian/trixie**: This branch contains qcom-adreno debian packaging rules and scripts for Debian Trixie.

## Typical Workflows

1. **Promote New Prebuilt Binary Version**: When new prebuilt binaries are available, the promote workflow updates upstream.conf in the packaging branch and opens a PR.
3. **PR validation**: PRs in this repo are validated against the package build to catch breakages early.
3. **Build Debian Package**: Once PRs get merged, the build debian package workflow builds debian packages for the corresponding packaging branch.
4. **Release Version**: A manual dispatch finalizes the changelog, builds the package, uploads artifacts to S3, and notifies [qcom-distro-images](https://github.com/qualcomm-linux/qcom-distro-images).

## Development

Refer to the [CONTRIBUTING.md](CONTRIBUTING.md) file for guidelines on contributing to this project.

## Usage

Build: To build the the package, go to *Actions* tab, select the *Build Debian Package* workflow, then 'Run workflow'

Upstream Version Promotion: ...

The workflows of this repo use the reusable workflows from qcom-build-utils in the background. To understand more how everything
connects together, see https://github.com/qualcomm-linux/qcom-build-utils

## Installation Instructions

1. Install common package, 
    - sudo dpkg -i qcom-adreno-common1_x_arm64.deb
2. For OpenCL,
    - sudo dpkg -i qcom-adreno-cl1_x_arm64.deb
3. For OpenGLESv1, OpenGLESv2 and EGL, 
    - sudo dpkg -i qcom-adreno-gles1_x_arm64.deb
    - sudo dpkg -i qcom-adreno-gles2_x_arm64.deb
    - sudo dpkg -i qcom-adreno-egl1_x_arm64.deb
4. For Vulkan,
    - sudo dpkg -i qcom-adreno-vulkan1_x_arm64.deb

## Getting in Contact

How to contact maintainers. E.g. GitHub Issues, GitHub Discussions could be indicated for many cases. However a mail list or list of Maintainer e-mails could be shared for other types of discussions. E.g.

* [Report an Issue on GitHub](../../issues)
* [Open a Discussion on GitHub](../../discussions)
* [E-mail us](mailto:Maintainers.pkg-qcom-adreno@qualcomm.com) for general questions

## License

pkg-qcom-adreno is licensed under the [BSD-3-Clause license](https://spdx.org/licenses/BSD-3-Clause.html). See [LICENSE.txt](LICENSE.txt) for the full license text.
