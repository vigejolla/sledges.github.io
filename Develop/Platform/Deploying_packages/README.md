---
title: Deploying packages
permalink: Develop/Platform/Deploying_packages/

---

## Deploying Packages

Once a package has been built, it must be deployed to the device (or SDK
target, in the case of -devel packages). Depending on whether the
package was built locally or remotely, there are different ways to
deploy the package to the device.

### Deploying Local RPMs

For packages built locally, the developer will have .rpm files which
they wish to deploy. To deploy these packages to the device, the
developer can first use `scp` to copy the .rpm from the host computer to
the device via ssh. Then, the package can be installed by issuing the
`rpm -Uvh --force <package.rpm>` command from a devel-su prompt (e.g.,
`devel-su rpm -Uvh --force <package.rpm>`). In some cases, rebooting the
device may be necessary to force any changes to take effect.

Note that packages installed in this fashion ("sideloaded") may cause
conflicts with packages installed from repositories. Future upgrades
will not necessarily succeed cleanly if a sideloaded .rpm with incorrect
version information is installed.

Some of the possible issues can be avoided by deploying with `zypper`,
pointing it to the directory where the .rpm files were copied using the
`-p|--plus-repo` option. New packages can be initially deployed with

`zypper -p `<rpms-dir>` -v in `<package>`...`

Packages that are already installed can be updated with

`zypper -p `<rpms-dir>` -v dup`

With this command zypper upgrades the system using the latest .rpm
packages found in <rpms-dir>. As `mb2` produces evergrowing version
numbers (unless told otherwise), this command always updates to the
latest built version found in the directory while obeying package
dependencies.

### Deploying From Repository

When the [Open Build Service](/Services/Development/Open_Build_Service) builds a
package, that package becomes available in a repository (usually, the
user's home project repository). The package may then either be
downloaded directly as an .rpm and installed as described in the above
section on deploying local .rpm files, or the repository can be added to
the device or SDK target as a [software update
repository](/Services/Deployment/SSU), and the device or SDK target can be updated
to install the package from that newly added repository.

The OBS repository can be added to the device or SDK target rootfs
repository via:

`ssu ar <repo_name> <repo_url>`

The available packages can then be installed to the device via

`devel-su pkcon refresh`

followed by

`devel-su pkcon install <pkg_name>`

or to the SDK via:

`zypper ref -f`

followed by

`zypper in <pkg_name>`

from an sdk-install-mode root prompt within ScratchBox2 (e.g., `sb2 -t
Sailfish OS-armv7hl -m sdk-install -R`).

You can use `ssu lr` to list the available repositories.
