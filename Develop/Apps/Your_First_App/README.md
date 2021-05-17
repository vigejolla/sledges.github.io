---
title: Your_First_App
permalink: Develop/Apps/Your_First_App/

---

## Your First App

If you don’t have the SDK installed and running yet, follow the
[installation guide](/Tools/Platform_SDK/Installation).

### Launch Sailfish OS IDE

You can launch from the ‘Sailfish OS IDE’ entry in the system menu (or
from `~/Sailfish OS/bin/qtcreator` if you’re a Linux terminal person).

As an example, on Ubuntu, open the dash, type in ‘sailfish’. Click on
the ‘Sailfish OS IDE’ icon to launch the IDE.

![Application\_sdk\_first\_app-ubuntu\_dash\_qtc.png](Application_sdk_first_app-ubuntu_dash_qtc.png
"Application_sdk_first_app-ubuntu_dash_qtc.png")

### Create a Sailfish UI Project

The SDK comes with a Sailfish UI template project that makes it very
easy to get started.

1\. In the IDE, click on **File→New File** or **Project**.

![Application\_sdk\_first\_app-qtc\_new\_project.png](Application_sdk_first_app-qtc_new_project.png
"Application_sdk_first_app-qtc_new_project.png")

2\. Select **Applications→Sailfish OS Qt Quick Application** and then
click **Choose**.

![Application\_sdk\_first\_app-qtc\_choose\_template.png](Application_sdk_first_app-qtc_choose_template.png
"Application_sdk_first_app-qtc_choose_template.png")

3\. Give a name to your project. Ensure it is created somewhere under
your home directory and click **Next**.

![Application\_sdk\_first\_app-qtc\_template\_01.png](Application_sdk_first_app-qtc_template_01.png
"Application_sdk_first_app-qtc_template_01.png")

4\. Select **MerSDK-Sailfish OS-armv7hl** (for ARM devices, e.g. the
Jolla phone) and **MerSDK-Sailfish OS-i486** (for Intel devices, e.g. the
emulator) kit and click Next.

![Application\_sdk\_first\_app-qtc\_template\_02.png](Application_sdk_first_app-qtc_template_02.png
"Application_sdk_first_app-qtc_template_02.png")

5\. You can edit the short description of your project or just click
**Next**.

![Application\_sdk\_first\_app-qtc\_template\_03.png](Application_sdk_first_app-qtc_template_03.png
"Application_sdk_first_app-qtc_template_03.png")

6\. Click **Finish**.

![Application\_sdk\_first\_app-qtc\_template\_04.png](Application_sdk_first_app-qtc_template_04.png
"Application_sdk_first_app-qtc_template_04.png")

7\. The project template is imported into your project and opened in the
editor.

![Application\_sdk\_first\_app-qtc\_open\_project.png](Application_sdk_first_app-qtc_open_project.png
"Application_sdk_first_app-qtc_open_project.png")

### Launch the Mer Build Machine and Emulator

The Sailfish OS SDK uses a Mer build machine to compile your code and
another virtual machine to run an emulator. If these are not running
when you attempt to build or deploy an application you will be asked to
start them.

> Note: The Mer build machine needs access to your source code to
> compile it and by default your home directory is shared – this is why
> the project should be in your home.

When a Sailfish OS project is open, the SDK automatically displays two
control buttons in the left toolbar for starting/stopping the Mer build
machine and Emulator.

![Application\_sdk\_first\_app-toolbar\_icons.png](Application_sdk_first_app-toolbar_icons.png
"Application_sdk_first_app-toolbar_icons.png")

1\. Click on the
![Application\_sdk\_faq-mersdk\_icon.png](Application_sdk_faq-mersdk_icon.png
"Application_sdk_faq-mersdk_icon.png") icon to launch Mer Build Engine.

The Mer Build Engine is started in the background and the icon will turn
gray until the machine has booted up.

2\. Click on the
![Application\_sdk\_faq-emulator\_icon.png](Application_sdk_faq-emulator_icon.png
"Application_sdk_faq-emulator_icon.png") icon to launch the emulator.
NOTE: This icon is only available if the MerSDK-Sailfish OS-i486 kit is
active. You can activate the MerSDK-Sailfish OS-i486 kit from menu
**Build → Open Build and Run Kit Selector…**.

A new VirtualBox window opens and boots up the emulator.

#### Successful connection

When the Qt Creator can successfully connect to both the emulator and
Mer build machine, the icons are updated as shown below.

Before connection:

  -   
    ![Application\_sdk\_first\_app-toolbar\_icons\_start.png](Application_sdk_first_app-toolbar_icons_start.png
    "Application_sdk_first_app-toolbar_icons_start.png")

Connection established:

  -   
    ![Application\_sdk\_first\_app-toolbar\_icons\_stop.png](Application_sdk_first_app-toolbar_icons_stop.png
    "Application_sdk_first_app-toolbar_icons_stop.png")

### Create a Connection to Sailfish OS Hardware Device

Sailfish OS SDK can also deploy application to Sailfish OS hardware
device. This feature requires a valid Sailfish OS hardware device to be
set-up with USB or WLAN connection to computer and making sure that it
is possible to connect to it over SSH with password. When using Sailfish
OS hardware device as development device in SDK a valid kit needs to be
selected (such as *Sailfish OS-armv7hl* target).

Sailfish OS hardware device setup is done using Qt Creator’s device
settings. Depending on your host environment this is found from either
the menu **Tools→Options→Devices** or **Qt
Creator→Preferences→Devices**. In this settings view, click **Add…**
to start creating device settings.

Unless some custom configuration is used, these default values work just
fine. If you encounter timeouts with SSH connections on your PC, you can
modify the timeout setting also after the device has been created.
Connect the device now, enter your SSH password and press Test
Connection as described in the dialog. On successful completion, you can
click Next to continue.

![Application\_sdk\_first\_app-mer\_hw\_select.png](Application_sdk_first_app-mer_hw_select.png
"Application_sdk_first_app-mer_hw_select.png")

In the next dialog, you can review and further adjust connection related
configuration. Click **Next** to continue.

![Application\_sdk\_first\_app-mer\_hw\_configure.png](Application_sdk_first_app-mer_hw_configure.png
"Application_sdk_first_app-mer_hw_configure.png")

In next dialog just click **Next** unless you want to abort device
creation. In that case click **Cancel**.

Qt Creator shall then create device configuration, deploy the SSH key to
device and finally test the setup. In those dialogs user can only click
**Close** to go to next phase.

Once tested and verified, Qt Creator shows a view which shows the
created device. Notice that configuration files are not updated yet, so
if you don’t press **OK** or **Apply** changes will not be saved.

That’s it. Now Qt Creator can deploy your application to device.

### Set ARM Kit to Deploy to Device

By default ARM kit will create RPM binaries, it won’t even try to deploy
to device. The deploy option **Build RPM Package for Manual Deployment**
is selected. This can be changed from Qt Creator’s main view with deploy
options, select **Deploy as RPM Package** or **Deploy by Copying
Binaries**.

![Application\_sdk\_first\_app-mer\_arm\_kit\_select\_deploy.png](Application_sdk_first_app-mer_arm_kit_select_deploy.png
"Application_sdk_first_app-mer_arm_kit_select_deploy.png")

Congratulations\! Now you can build and deploy to Sailfish ARM device.

### Build and Deploy the App

Press the
![Application\_sdk\_first\_app-qtc\_run\_button.png](Application_sdk_first_app-qtc_run_button.png
"Application_sdk_first_app-qtc_run_button.png") button in the toolbar to
compile and run the project on the emulator.

That’s it\! You just ran your first Sailfish OS application. It should
be running in the emulator as shown below.

![Application\_sdk\_first\_app-emulator\_screenshot\_01.png](Application_sdk_first_app-emulator_screenshot_01.png
"Application_sdk_first_app-emulator_screenshot_01.png")

#### Build RPM Package for Manual Deployment

The default deploy option is to only build RPM packages. In this case
the Run and Debug buttons are replaced with single Deploy button, that
can be used to create the RPM packages. Alternatively the menu **Build →
Deploy Project “projectname”** can be used to trigger package creation.

Next steps: exploring how to [use the
application](/Develop/Apps/Using_Sailfish_OS_Apps).
