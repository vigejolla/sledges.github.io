---
title: Development
permalink: Services/Development/

---

Development for Sailfish OS involves a number of web services to track
development tasks, integrate features and bug fix patches into the code
mainline, and process built packages for testing and release.

The main services in this process are:

  - [Bugzilla](/Services/Development/Bugzilla): An issue tracking service. All
    identified tasks and bugs are tracked and triaged here.
  - [Git Server](/Services/Development/Sailfish_OS_Source): A git server allowing users to
    submit code changes.
  - [Webhooks](/Services/Development/Webhooks): A service that accepts git change
    triggers from git servers and triggers builds in OBS.
  - [Open Build Service](/Services/Development/Open_Build_Service) (OBS): An
    automated build system that takes source code from a git server and
    produces standalone packages from the source repositories.
  - [Image Creator](/Services/Development/Image_Creator): A service to build clean
    and shareable system images for development, testing and release.

For example, a say a bug is identified in the mer-core
[lipstick](https://git.sailfishos.org/mer-core/lipstick) package. To fix
this bug:

  - A bug is filed in the [Mer Bugzilla](https://bugs.merproject.org/)
    service to track the issue and assigned to a developer for fixing.
  - The developer creates a patch to fix the bug, pushes the change to
    the relevant git server repository in
    <https://git.sailfishos.org/mer-core/lipstick>, and creates a Merge
    Request to merge the change into the mainline branch. Other
    developers can then review this request and approve it if the change
    is satisfactory, or provide feedback if it should be improved.
  - Once the change is approved, it is merged into the code mainline,
    and tagged with *git tag* using the current package version number
    to indicate that a new *lipstick* package needs to be built. The
    webhook for the repository detects that there is a new tag, and
    notifies OBS.
  - The Mer [Open Build Service](/Services/Development/Open_Build_Service) takes
    the source code from the git server and produces a new build of the
    *lipstick* package for all supported Sailfish OS platforms. If the
    package cannot be built on all platforms, OBS sends a notification
    of the build error and the details. Otherwise, the package is
    accepted into the collection of latest build packages.
  - The Mer [Image Creator](/Services/Development/Image_Creator) builds a new
    device system image using packages fetched from OBS, including the
    freshly updated *lipstick* package. If the image is successfully
    built, it is ready to be flashed onto a device for testing or
    further development.

For more information about filing bugs, and contributing fixes to
issues, please see the [Collaborative
Development](/Develop/Collaborative_Development) documentation.
