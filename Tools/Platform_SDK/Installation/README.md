---
title: Installation
permalink: Tools/Platform_SDK/Installation/

---

## SDK Installation

We provide a graphical installer to make it easy to setup the Sailfish
SDK.

### Common pre-requisites

  - Virtualization platform. On Linux and Windows, both Oracle
    VirtualBox (version 4.1.18 or higher) and Docker (version 18.09.3 or
    higher) are supported. On MacOS, only VirtualBox is supported. On
    Linux, you should install the virtualization platform packages
    supplied by your distribution. On other operating systems, we
    recommend using installation packages from
    <http://www.virtualbox.org> or
    <https://hub.docker.com/search/?q=&type=edition>
  - For emulator you need Oracle VirtualBox regardless of your choice of
    virtualization for the build engine
  - About 5GB of free disk space.
  - 4GB of RAM or more is recommended.

#### SDK Installer on Linux

1.  [Download](/Application_SDK#Latest_SDK_Release) the run
    file
2.  Open the Terminal application on your host system.
3.  Provide executable permissions to it: `$ chmod +x
    ~/Downloads/`<installer_name>
4.  Run the installer as a normal user (i.e. not as root user). By
    default it will install to `Sailfish OS/` in your home directory.

<!-- end list -->

  -   
    `$ ./Downloads/`<installer_name>

#### SDK Installer on Windows

1.  Ensure Git is installed
      - Git for Windows can be obtained from
        <https://git-scm.com/download/win>
2.  [Download](/Application_SDK#Latest_SDK_Release) SDK
    Installer application (Currently supported platforms include Windows
    7 and 10) to your downloads folder and locate it with Explorer.
3.  Open SDK installer by double-clicking the SDK Installer application.

#### SDK Installer on OS X

1.  [Download](/Application_SDK#Latest_SDK_Release) SDK
    Installer package.
2.  Open SDK Installer package by double-clicking the icon.
3.  Open the SDK Installer application found from the package.

### Common installation flow

The SDK installer window will open as shown below. The installation
itself is pretty simple.

![Application\_sdk\_installation-installer\_01.png](Application_sdk_installation-installer_01.png
"Application_sdk_installation-installer_01.png")

Click **Next**, follow the setup wizard and read and accept the license
agreement. The default values are usually OK. If you wish, you can see
the details of the files being installed. After a successful
installation you should see a window like the one shown below.

![Application\_sdk\_installation-installer\_02.png](Application_sdk_installation-installer_02.png
"Application_sdk_installation-installer_02.png")

Click **Finish**. The Sailfish IDE launches automatically once the setup
wizard exits.

### Launching the Sailfish IDE

  - The SDK will be added to your system menus and a launch icon will be
    available for future sessions.
  - On Linux you can launch the Sailfish IDE from desktop launcher by
    typing `Sailfish IDE` and choosing the appropriate icon.
    Alternatively, you can stat it from command line by running
    `~/Sailfish OS/bin/qtcreator`.
  - On Windows you can launch the Sailfish IDE by pressing Start and
    typing `Sailfish IDE` and choosing the appropriate application.
  - On OS X you can launch the Sailfish IDE by opening Launchpad and
    typing `Sailfish IDE`. (With Spotlight it can be found by typing `Qt
    Creator`.)
  - Once SDK is installed, proceed to creating your first application\!
