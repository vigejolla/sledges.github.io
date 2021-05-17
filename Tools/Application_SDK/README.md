---
title: Application SDK
permalink: Tools/Application_SDK/

---

# Sailfish SDK

## Latest SDK Release

The latest Sailfish SDK release can be downloaded for Linux, OS X and
Windows platforms from below.

<big>

### **Sailfish SDK 3.4**

|                                                                                                        |                                                                                                    |                                                                                                          |
| ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| [**Linux**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-linux64-online.run) | [**macOS**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-mac-online.dmg) | [**Windows**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-windows-online.exe) |

</big>

After downloading the SDK for your platform, please follow through with
the [installation
instructions](/Tools/Platform_SDK/Installation).

### Release Notes

The release notes for this SDK release are available at
[1](https://forum.sailfishos.org/t/4924).

### All Download Options

| Filename                                                                                                                                | Size                    | MD5 Hash                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| [**SailfishSDK-3.4.9-linux64-online.run**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-linux64-online.run)   | 28M (28880459 bytes)    | [**4d80ddf674c835432c79a4535c4002d8**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-linux64-online.run.md5)  |
| [**SailfishSDK-3.4.9-linux64-offline.run**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-linux64-offline.run) | 1.5G (1507173573 bytes) | [**fdd6a0a2e8532b3aa510abf6149f3b8f**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-linux64-offline.run.md5) |
| [**SailfishSDK-3.4.9-mac-online.dmg**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-mac-online.dmg)           | 11M (11525405 bytes)    | [**c05e62450981127abf675a0046ff4564**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-mac-online.dmg.md5)      |
| [**SailfishSDK-3.4.9-mac-offline.dmg**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-mac-offline.dmg)         | 1.4G (1495293138 bytes) | [**a56e897b30c6522fdecbd6bc5c49d076**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-mac-offline.dmg.md5)     |
| [**SailfishSDK-3.4.9-windows-online.exe**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-windows-online.exe)   | 20M (20791121 bytes)    | [**fbe7b30d2a4ff3f7cb0c8d1401a5d705**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-windows-online.exe.md5)  |
| [**SailfishSDK-3.4.9-windows-offline.exe**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-windows-offline.exe) | 1.4G (1450583478 bytes) | [**7c665ee50cf1dac426a43415eb346b1d**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-windows-offline.exe.md5) |

Offline installers allow Sailfish SDK installation with VirtualBox-based
build engine, latest build targets and latest emulator on hosts with
limited network access.

## Early Access

### EA SDK

You can get the SDK updates approximately a week or two earlier, if you
start using the Early Access repository. This can be useful for e.g.
testing the new SDK features before the final Sailfish SDK release.
Check out for more information from the [Early Access SDK
page](/Develop/Apps/Early_Access).

### EA Build Targets

You can get the build target updates approximately a week earlier, if
you install an Early Access build target or targets into your SDK. This
can be useful for e.g. testing your apps before the official public
Sailfish OS release. Check out for more information about the [Early
Access Build
Targets](/Develop/Apps/Early_Access).

## Guides

### SDK

  - [Application SDK
    Installation](/Tools/Platform_SDK/Installation)
  - [Application SDK
    Uninstallation](/Develop/Apps/Uninstallation)
  - Application SDK Guides
      - [Your First App](/Develop/Apps/Your_First_App)
      - [Using Sailfish OS
        Apps](/Develop/Apps/Using_Sailfish_OS_Apps)
      - [Code Walkthrough](/Develop/Apps/Code_Walkthrough)
      - [Packaging Apps](/Develop/Apps/Packaging)
  - [Application SDK Known
    Issues](/Develop/Apps/Known_Issues)
  - [Application SDK FAQ](/Develop/Apps/FAQ)

### Sailfish OS

  - [Sailfish OS
    Tutorials](/Develop/Apps)

## Supported Environments

Our SDK has been verified on the following systems:

  - Ubuntu 18.04 64 bit
  - Windows 10 32/64 bit
  - OS X 10.12.6
  - It should work on other Linux flavours as well, but at this stage,
    its functionality on other host environments has not been fully
    verified. See also Pre-requisites below.

Pre-requisites:

  - A host machine running a Linux/Windows/OS X operating system.
  - Oracle’s VirtualBox version 4.1.18 or higher pre-installed on the
    host machine. You should use the VirtualBox that is compatible with
    your distribution.
  - Git is a prerequisite for the Sailfish SDK on Windows. Git for
    Windows can be obtained Git from <https://git-scm.com/download/win>
  - About 5GB of free disk space.
  - 4GB of RAM or more is recommended.
  - libtinfo.so.5 - not all distributions ship this library by default.
      - On Ubuntu 20.04, the package libtinfo5 may be installed.
      - On Fedora the package ncurses-compat-libs may be installed
      - If you find no way to fix libtinfo.so.5 on your system, you may
        try creating it as a symbolic link to your system
        libncurses.so.5 (or even libncurses.so.6 or libtinfo.so.6)

## Contact us

If you have any questions, feel to contact us in
<https://forum.sailfishos.org/>.
