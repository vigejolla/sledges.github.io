---
title: Early_Access
permalink: Develop/Apps/Early_Access/

---

# Early Access SDK

Sailfish SDK Early Access releases will provide the new SDK features and
fixes a week or two before the final SDK release. By using the Early
Access SDK you can be sure to get the latest and greatest SDK features
first.

If you are looking for the regular SDK release or general information
about the SDK itself, check out the [Application
SDK](/Tools/Application_SDK) page.

## Early Access Build Targets

The early access build targets are supported in both the Sailfish SDK
and Sailfish SDK Early Access releases.

The latest early access targets can be installed by using the
SDKMaintenanceTool:

1\. Open the **SDKMaintenanceTool**

2\. Choose **Add or remove components** and click **Continue**

3\. Click the **Sailfish OS Build Targets** branch open from the
components list

4\. **Check** `Sailfish OS-ea-armv7hl` and/or `Sailfish OS-ea-i486`
component(s) for installation

5\. Click **Continue** and follow through with the installation

The early access build targets will be released in sync with the early
access releases of the Sailfish OS. Generally these releases will be
available about a week earlier than the official public release. This
allows developers to test and refine their apps before the public
release.

If you have installed an early access build target or targets by using
the SDKMaintenanceTool, you will get an update notification
automatically when a newer early access build target release is
available.

Please, remember, that the Early Access build targets should not be used
for submitting apps to the Jolla Harbour. For that purpose, you should
always use the latest non-EA (`Sailfish OS-latest-armv7hl` or
`Sailfish OS-latest-i486`) build targets.

## Latest Early Access SDK Release

The latest Sailfish SDK Early Access release can be downloaded for
Linux, macOS and Windows platforms from below.

<big>

### **Sailfish SDK 3.4**

|                                                                                                        |                                                                                                    |                                                                                                          |
| ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| [**Linux**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-linux64-online.run) | [**macOS**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-mac-online.dmg) | [**Windows**](https://releases.sailfishos.org/sdk/installers/3.4.9/SailfishSDK-3.4.9-windows-online.exe) |

</big>

**Please, read the section [Installing the Early Access
SDK](/Develop/Apps/Early_Access)
before using these installers. The Early Access SDK repository should be
taken into use before installation.**

### Release Notes

The release notes for this SDK release are available at [Sailfish OS
Forum](https://forum.sailfishos.org/t/4924).

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

## Installing the Early Access SDK

1\. Open the **Sailfish OS SDK Installer**

2\. Click **Settings**

3\. Go to the **Repositories** page

4\. **Uncheck** (Disable) the `updates` repository

5\. **Check** (Enable) the `updates-ea` repository

6\. Click **OK** and continue with the [installation
instructions](/Tools/Platform_SDK/Installation)

## Receiving Early Access SDK Updates Automatically

If you want to receive the Early Access SDK updates automatically,
enable the Early Access repository in your SDK:

1\. Open the **SDKMaintenanceTool**

2\. Choose **Update components**

3\. Click **Settings**

4\. Go to the **Repositories** page

5\. **Uncheck** (Disable) the `updates` repository

6\. **Check** (Enable) the `updates-ea` repository

7\. Click **OK** and check for updates
