---
title: Uninstallation
permalink: Develop/Apps/Uninstallation/

---

## SDK Uninstallation

The Sailfish OS SDK comes with a maintenance tool, named
`SDKMaintenanceTool` that can be used to remove the complete
installation (for Windows 8 read [known
issues](/Develop/Apps/Known_Issues)). You can find it
listed in your host distribution’s system menu or directly in the
installed directory, for example in Linux `~/Sailfish OS`.

### Pre-requisites

  - The emulator and Mer SDK virtual machines are powered off.
  - The VirtualBox software is not running.
  - The Sailfish OS IDE (Qt Creator) is not running.

### Uninstallation

Run the SDKMaintenanceTool

  - On Linux open terminal and type `$ ~/Sailfish OS/SDKMaintenanceTool`
  - On Windows press Start and type `SDKMaintenanceTool`
  - In OS X open Spotlight (cmd+space) and type `SDKMaintenanceTool`

Select **Remove all components** and click **Next**.

![Application\_sdk\_uninstallation-uninstall\_01.png](Application_sdk_uninstallation-uninstall_01.png
"Application_sdk_uninstallation-uninstall_01.png")

Follow the instructions on the wizard. Once the uninstallation has
completed successfully, you will see the following screen. Click
**Finish** to exit the wizard.

![Application\_sdk\_uninstallation-uninstall\_02.png](Application_sdk_uninstallation-uninstall_02.png
"Application_sdk_uninstallation-uninstall_02.png")
