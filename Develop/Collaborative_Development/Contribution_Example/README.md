---
title: Contribution Example
permalink: Develop/Collaborative_Development/Contribution_Example/

---

This document describes contribution example how to contribute the code:

For this example, we will consider a hypothetical bug which affects the
Sailfish Browser. The community member "Alice" discovers that for some
content-aggregator sites, the wrong User Agent string seems to be used
when fetching content. She decides to investigate and contribute a fix.
These are the steps she takes:

1\) She files an issue on
<https://github.com/sailfishos/sailfish-browser/issues> with example
issue template from above.

2\) She comments on the issue to say that she will investigate the
issue.

3\) She searches for the upstream code repository, and finds
<https://github.com/sailfishos/sailfish-browser> and notes that it
depends on embedlite-components-qt5. After browsing that source code,
she realises that the user agent override behaviour is defined in code
from the embedlite-components-qt5 package.

4\) She searches for that package on build.sailfishos.org and finds
<https://build.sailfishos.org/package/show/mer-core:devel/embedlite-components-qt5>
whose \_service file shows the upstream repository URL
<https://git.sailfishos.org/mer-core/embedlite-components.git>

5\) She creates a personal fork of that repository using the web
interface at <https://git.sailfishos.org/mer-core/embedlite-components/>

6\) She clones that personal fork to her local host machine via \`git
clone <ssh://git@git.sailfishos.org:2222/alice/embedlite-components.git>
alice-embedlite-components\`

7\) She builds the package

`   # cd into her local clone`  
`   ~ $ cd alice-embedlite-components`

`   # enter Platform SDK chroot`  
`   ~/alice-embedlite-components $ /srv/mer/sdks/sdk/mer-sdk-chroot`

`   # attempt to build the package for her Sailfish OS-armv7hl target`  
`   PlatformSDK ~/alice-embedlite-components $ mb2 -t Sailfish OS-armv7hl build`  
`   No provider of 'xulrunner-qt5-devel >= 31.7.0.14' found.`  
`   Building target platforms: armv7hl-meego-linux`  
`   Building for target armv7hl-meego-linux`  
`   error: Failed build dependencies:`  
`       xulrunner-qt5-devel >= 31.7.0.14 is needed by embedlite-components-qt5-1.0.0-1.armv7hl`  
`       pkgconfig(nspr) is needed by embedlite-components-qt5-1.0.0-1.armv7hl`

`   # she knows that she needs to update her SDK target.`  
`   # to find out which ssu repository provides those packages, she now ssh's into her device,`  
``   # and runs `zypper info` (can also use `pkcon get-details` or search on OBS).``  
`   ~/alice-embedlite-components $ ssh nemo@device`  
`   [nemo@Sailfish OS ~]$ zypper info xulrunner-qt5-devel`  
`   Loading repository data...`  
`   Reading installed packages...`  
`   Information for package xulrunner-qt5-devel:`  
`   --------------------------------------------`  
`   Repository: apps-mw`  
`   Name: xulrunner-qt5-devel`  
`   Version: 31.8.0.8-10.44.19.jolla`  
`   Arch: armv7hl`  
`   Vendor: meego`  
`   Installed: No`  
`   Status: not installed`  
`   Installed Size: 31.5 MiB`  
`   Summary: Headers for xulrunner`  
`   Description: `  
`     Development files for xulrunner.`

`   # she now knows that it comes from the "apps-mw" repository.`  
`   # she goes back to her Platform SDK chroot terminal, and`  
`   # enters ScratchBox2 to update the ssu repositories.`  
`   PlatformSDK ~/alice-embedlite-components $ sb2 -t Sailfish OS-armv7hl -m sdk-install -R`

`   # might be required to register her SDK depending on her SDK setup.`  
`   [SB2 sdk-install Sailfish OS-armv7hl] user@host alice-embedlite-components # ssu r`

`   # list the available repos`  
`   [SB2 sdk-install Sailfish OS-armv7hl] user@host alice-embedlite-components # ssu lr`  
`   ## snipped ##`  
`   Disabled repositories (global, might be overridden by user config):`  
`    - apps-mw ... `<https://download.jollamobile.com/pj:/apps:/mw/latest_armv7hl/>  
`   ## snipped ##`

`   # she enables the repository.`  
`   [SB2 sdk-install Sailfish OS-armv7hl] user@host alice-embedlite-components # ssu er apps-mw`

`   # she refreshes the available package list`  
`   [SB2 sdk-install Sailfish OS-armv7hl] user@host alice-embedlite-components # zypper ref -f`

`   # she installs the required packages into her SDK target`  
`   [SB2 sdk-install Sailfish OS-armv7hl] user@host alice-embedlite-components # zypper in xulrunner-qt5-devel nspr-devel`

`   # now she is ready to go back to the PlatformSDK chroot and use mb2 to build the package again.`  
`   [SB2 sdk-install Sailfish OS-armv7hl] user@host alice-embedlite-components # exit`  
`   PlatformSDK ~/alice-embedlite-components $ mb2 -t Sailfish OS-armv7hl build`  
`   # success!`  
`   PlatformSDK ~/alice-embedlite-components $ exit`

8\) Now that she has successfully built the package locally, she tests
deploying the package.

`   ~/alice-embedlite-components $ scp RPMS/embedlite-components-qt5-1.0.0-1.armv7hl.rpm nemo@device:~/`  
`   ~/alice-embedlite-components $ ssh nemo@device`  
`   [nemo@Sailfish OS ~]$ devel-su rpm -Uvh --force embedlite-components-qt5-1.0.0-1.armv7hl.rpm`

9\) After rebooting the device and opening browser, she sees that it
works. She is now ready to begin development. She makes changes, adds
debug statements, deploys the package to the device, and retrieves the
logging information from the journal with \`devel-su journalctl -af |
grep browser\`.

10\) After she has resolved the issue, and commits her fix locally. She
then pushes the commit to her personal fork, and creates a merge request
to the upstream repository. This will look something like
<https://git.sailfishos.org/mer-core/embedlite-components/merge_requests/7>

11\) She now updates the issue report with her findings, and a link to
her merge request.

12\) After receiving some review comments, she updates her commit with
\`git commit --amend\`, force pushes it to her personal fork via \`git
push origin master:master --force\` and comments in the merge request
that it has been updated.

13\) The maintainer merges the patch, tags it, and comments on the
original bug report the tagged version which should be in a future
release.
