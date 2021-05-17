---
title: Building packages
permalink: Develop/Platform/Building_packages/

---

## Building Packages

Packages may either be built locally (using `mb2` or `sb2` using the
Platform SDK), or remotely (using the Mer OBS). Building locally has the
advantage of being quick, simple, and low-latency. Building remotely has
the advantage that build dependencies and other packaging requirements
are enforced more strictly, and that upgrading packages built from OBS
can be done via system upgrade rather than sideloaded via direct
installation using \`rpm\`.

### Building Packages Remotely

Packages may be built using the [Open Build
Service](/Services/Development/Open_Build_Service) instance. This requires the user
to create a home project, and then create a package under that project,
with the appropriate \`\_service\` file to specify how the project
should be built and packaged. Once the build has been triggered, OBS
will attempt to pull in the required dependencies and build the package.

See the page about [deploying packages](/Develop/Platform/Deploying_packages)
for information on how to install the package once built.

### Building Packages Locally

Once the user has installed the [Platform
SDK](/Tools/Platform_SDK/Installation) and set up an [SDK
target](/Tools/Platform_SDK/Target_Installation), they can build
packages locally for the target architecture using the build script
called `mb2` invoked from the Platform SDK. This script is a wrapper
around ScratchBox2 (`sb2`) and `rpmbuild` which makes it simple to build
packages from source repositories, given an RPM specification (.spec)
file.

The mb2 script is invoked as follows to build a package:

`mb2 -s <path/to/rpm.spec> -t `<SDK_target>` build`

Note that the first two parameters are optional if there is only one
single .spec file contained under the rpm/ subdirectory of the project.

For example, the following command will build most projects and package
the results into an .rpm ready for installation, when run from the
Platform SDK chroot prompt, within the project directory, assuming that
an SDK target called "Sailfish OS-armv7hl" has been installed:

`mb2 -t Sailfish OS-armv7hl build`

The output .rpm files will be contained under the RPMS/ subdirectory of
the project. Alternatively it is possible to use the `-o|--outputdir`
option to let `mb2` store .rpm files in a common directory for easier
deployment.

`mb2 -t Sailfish OS-armv7hl -o ~/RPMS build`

These .rpm files may be installed to the device or SDK target as
described in the page on [deploying
packages](/Develop/Platform/Deploying_packages).

Please check further documentation, for example how to build debug
packages, with

`mb2 --help`

#### Installing Missing Dependencies

In some cases, the developer will have to add or enable repositories
within their SDK target, if the `mb2` script complains that a dependency
cannot be installed. To do so, the user should enter ScratchBox2 within
the SDK chroot environment, and then use:

`ssu ar <repo_name> <repo_url>`

to add repositories, and

`ssu er <repo_name>`

to enable repositories, and then

`zypper ref -f`

to update the installable package information. `ssu lr` may be used to
list known repositories, and ` ssu rr  `<repo_name> will remove a
repository.

Example:

`# enter the Platform SDK chroot`  
`~ $ /srv/mer/sdks/sdk/mer-sdk-chroot`  
  
`# enter ScratchBox2 root shell in sdk-install mode`  
`PlatformSDK ~ $ sb2 -t Sailfish OS-armv7hl -m sdk-install -R`  
  
`# enable the mer-core repository if not already enabled`  
`[SB2 sdk-install Sailfish OS-armv7hl] ~ # ssu er mer-core`  
  
`# reload the package list`  
`[SB2 sdk-install Sailfish OS-armv7hl] ~ # zypper ref -f`

To determine which repository provides a given package, a contributor
should use the search feature of the Mer OBS instance, at
<https://build.merproject.org/search>

It should be noted that device or hardware-platform-specific packages
(especially those needed to build hybris-related packages) are best
installed into a separate SDK target, to avoid complications. See
[Platform SDK Target
Installation](/Tools/Platform_SDK/Target_Installation) for more
information on how to create new SDK targets.

#### Clean Builds

It is possible to avoid polluting build targets with build time
dependencies of a particular package by using `mb2` with its
`--snapshot` option. With this option the build target is not used
directly. Instead a snapshot is taken and the build is done using the
snapshot of the build target.

Consider enabling the `--snapshot` by default by creating an alias in
your `~/.mersdk.profile`:

`alias mb2='mb2 --snapshot'`

Check `mb2 --help` output for more details.

## Building Binaries Locally

In some cases, you will not want to build an entire package (.rpm) to
install, but instead want to build a single binary from a simple (most
likely Qt-based) project. This can be handy, for example, during testing
or prototyping.

In this case, you simply need to build the project from within a
build-mode ScratchBox2 prompt. For example, to build a simple Qt-based
project (called "test", located under \~/test/ of the host) the
following steps could be taken:

`# enter the Platform SDK chroot`  
`~ $ /srv/mer/sdks/sdk/mer-sdk-chroot`  
  
`# enter ScratchBox2 shell in sdk-build mode`  
`PlatformSDK ~ $ sb2 -t Sailfish OS-armv7hl -m sdk-build`  
  
`# run qmake && make from within sb2 build prompt`  
`[SB2 sdk-build Sailfish OS-armv7hl] ~ $ cd ~/test && qmake && make`

The resulting ARMv7 binary can be copied to the device with `scp` and
executed directly.

## Packaging formats

There are different repository formatting guidelines for automated
building and packaging for Sailfish OS, depending on the relationship
between that repository and its upstream origin and state.

### tar\_git packaging structure

A special OBS service called 'tar\_git' can automatically package
sources from a specifically formatted git repository along with any
referenced git submodules into a suitable tar archive to be built on
OBS. This format is relatively simple and as long as one follows some
basic instructions tools like `mb2` work nicely and if `mb2` works then
it is quite likely that also the package builds fine after integrating
as part of the release process. This process can be triggered
automatically on OBS when a new git tag is created, using
[Webhooks](/Services/Development/Webhooks).

Some basic things to remember: the rpm .spec files are located in
`rpm/*.spec`. As described below. the changelog is generated from git
commit messages, so there is no need to include a changelog section in
the spec file nor a separate .changes file, unless pre-git historical
changelog entries need to be included. These can be included in
`rpm/*.changes` files. All other files in `rpm/` directory must be
marked either with **SourceX:** or **PatchX:**. Package version is
determined from the latest suitable Git tag. The **Version:** and
**Release:** tags in the .spec file are ignored – setting them to "0"
and "1" respectively is the preferred convention.

Packaging should aim to preserve upstream git history whenever possible
to allow for easier synchronization of upstream changes. Bearing this in
mind, there are several possibilities for packaging, depending on
whether there is an upstream repository and the number of modifications
of it required for the Sailfish OS version.

#### tar\_git package source code location in git

When a package has no upstream, i.e. is a package maintained as part of
Sailfish OS, the sources are usually located solely within a single git
repository alongside the rpm directory, either in the root of the git
tree or src dir or something similar depending a bit on the package.
Example of such package is for example the lipstick display manager at
<https://git.sailfishos.org/mer-core/lipstick/tree/master>

Otherwise, the package should contain a link to its upstream repository
as a git submodule, named the same as the package **Name:** in .spec
file, or simply as **upstream**. Please use https format for git
submodule url. This makes sure that submodule cloning works for all
users. Third-party repositories should be mirrored on
<https://git.sailfishos.org/mirror> and referenced there, to avoid
future build errors due to upstream moves or removal. New repository
mirrors can be requested on IRC.

If the package has upstream somewhere else and there are no heavy
modification needed for the sources, the sources are usually built
directly from the git submodule. Small modifications and backported
commits from later versions can be included as patches stored as
`rpm/*.patch`. Locally, those patches can be applied with `mb2 apply` to
the submodule or as part of the whole prepare phase using `mb2 prepare`.
They can be unapplied with `mb2 apply -R`. PackageKit is an example of
such package at
<https://git.sailfishos.org/mer-core/PackageKit/tree/master>

There is a proposal to use a long-lived topic branch instead of patches,
which mirrors the upstream repository directly rather than using a
submodule. See
[Git\_Packaging\_-\_Upstream\_Git\_with\_Long-Lived\_Topic\_Branch\_Approach](/Develop/Platform/Git_Packaging_-_Upstream_Git_with_Long-Lived_Topic_Branch_Approach).

If there are many modifications to the upstream that are not accepted as
a part of the upstream (at least yet), then they may be stored in a
separate tree from the upstream submodule. In such cases the submodule
should be called **upstream** and the modified copy of the upstream
should be a separate directory named after the package name from the
.spec file. Synchronization with newer upstream releases is done using
[`git`` 
 ``subtree`](/Usage_of_packaging_formats#Upstream_git_with_subtrees).
An example of such a package is 'connman' at
<https://git.sailfishos.org/mer-core/connman/tree/master>.

### Dumb packages

This is an obsolete format and that generally should not be used any
more. Any packages using this should be converted to tar\_git format
whenever the opportunity arises. These use no smart packaging system,
instead storing the .spec file, tarball and any patches directly in the
root of the git tree. One situation where this might be preferable is if
there is no upstream version control and only source tar downloads are
available, in which case that archive may be used without modification.
An example of such packaging is ncurses, found at
<https://git.sailfishos.org/mer-core/ncurses/tree/master> .

Such 'dumb' packages do not compile with the normal `mb2` as the
packages done with tar\_git format, but these need to be build with more
conventional tools, for example:

    git clone https://git.sailfishos.org/mer-core/example-dumb-package.git
    cd example-dumb-package
    sb2 -t Sailfish OS-armv7hl
    rpmbuild --define "_topdir `pwd`" --define "_sourcedir `pwd`" -bb *.spec

instead of `mb2 build`.

Should be noted that when using `rpmbuild` you need to manually install
also package build dependencies, where `mb2` does that automatically.

## Changelog generation

Changelogs are generated from git commits (or from annotated tags in
case on forgets the message from the commit) in tar\_git packaged
packages. This allows change logs to be generated automatically, and for
the commit history to contain meaningful back-links to the bug reports
which led to the change being made.

Basically how it works is that each line that has the `[ ]` is added to
the changelog of the package and rest of the lines from the commit
message are ignored:

    [SHORT] Long description that shall reflect the work done. Bug-ref JB#xxxx
    [key] Summary. Contributes to xyz#123
    [packaging] Updated Y to version X. Fixes xyz#124

**NOTE: Run `mb2 --help` inside the SDK to learn how to generate
changelogs when building a package with mb2 locally**

This line does not need to be the first line in the git commit message
and there can be multiple lines within one git commit message.

The **SHORT** description is any descriptive word like "backend" or "UI"
or "bluetooth". Long description describes the change in plain English
and shall contain a reference to a bug.

There are couple of ways to refer bugs in the git commit messages

|                         |                                                                                                                                                                                                                                                                                                                            |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Contributes to xyz\#123 | Means that this change contributes to the referred bug number, but does not fully fix it yet. This kind of lines are usually used when the required fixes to one bug are needed across multiple packages or for example the fix improves the issue, but there might still be some corner case that it might be reproduced. |
| Fixes xyz\#124          | Means that this change fixes the bug.                                                                                                                                                                                                                                                                                      |

Currently known and accepted bug tags for the above **xyz** are:

|      |                                                                      |
| ---- | -------------------------------------------------------------------- |
| MER  | For bugs at <https://bugs.merproject.org/>                           |
| NEMO | For bugs at <https://bugs.nemomobile.org/>                           |
| JB   | For bugs in internal Jolla Bugzilla                                  |
| TJC  | To reference issues listed in [together](https://together.jolla.com) |

These lines are picked to the changelog based on tags, meaning that
between two tags all the lines that are following the format are picked
up and added to the changelog.
