---
title: Architecture
permalink: Reference/Architecture/

---

## Overview

Sailfish OS is a mobile operating system based on GNU/Linux.

The Sailfish OS architecture is primarily made up of three areas
hardware adapation layer, the middleware layer and the app/UI layer:

<div style="margin:auto; width:80%; text-align:center;">

<div class="btn-sec" style="margin:auto; width:80%; text-align:center;">

Applications

</div>

<div class="btn-sec" style="margin:auto; width:80%; text-align:center;">

Lipstick Homescreen and UI management

</div>

  

</div>

<div style="margin:auto; width:80%; text-align:center;">

<div class="btn-sec" style="margin:auto; width:80%; text-align:center;">

Qt application framework

</div>

<div class="btn-sec" style="margin:auto; width:80%; text-align:center;">

Other middleware libraries and services

</div>

  

</div>

<div style="margin:auto; width:80%; text-align:center;">

<div class="btn-sec" style="margin:auto; width:80%; text-align:center;">

Hardware adaptation components

</div>

<div class="btn-sec" style="margin:auto; width:80%; text-align:center;">

Kernel

</div>

  

</div>

## Hardware Adaptation layer

In the hardware adaptation layer, Sailfish OS uses a Linux kernel with
hardware-specific additions.

Sailfish OS can run on top of standard Linux hardware with native
drivers, or one can utilize the drivers for an Android-compatible
hardware via [libhybris](https://github.com/libhybris), which bridges
Linux libraries (based on GNU C) with those based on Bionic, such as
Android. Building an adaptation for Android-compatible hardware is
instructed in [
HADK](/Hardware_Adaptation_Development_Kit#Hardware_Abstraction_Layer)
documentation.

## Middleware layer

In the middleware layer there are core system components for building
services above hardware layer.

The [Qt](http://www.qt.io) C++ application development framework
provides the primary development libraries. Aside from the main Qt
modules, Sailfish OS uses add-on modules such as Qt Maps, Qt Sensors and
Qt Contacts. Also, all Sailfish applications are written with
[QML](http://doc.qt.io/qt-5/qmlapplications.html), a Qt technology for
easily building user interfaces into C++ applications.

Sailfish OS also includes a large range of middleware libraries and
frameworks that service the application layer, more details on the
location for the sources please refer to
[Sailfish OS\_Source\#Sailfish\_OS\_Source](/Services/Development/Sailfish_OS_Source).
They are written in C/C++, and libraries that are directly accessed by
the UI layer include QML modules to allow them to be used by QML-based
applications without additional QML/C++ bindings.

## Application and UI layer

Sailfish OS applications are
[written](/Develop/Apps) in a combination of C++
and [QML/Qt Quick](http://doc.qt.io/qt-5/qmlapplications.html). QML is a
Qt technology primarily used to declaratively assemble application user
interfaces and connect them to C++ backend code, and Qt Quick is a core
part of the QML framework for UI creation. A Sailfish OS app typically
defines the UI in QML, and if necessary, includes C++ utility code to
execute further functionality that is otherwise unavailable from the QML
layer.

Application launching and lifetime is controlled by
[Lipstick](/Reference/Core_Areas_and_APIs/Apps_and_MW/Lipstick), which provides the essential
user-session UI with an application launcher and other main screens, and
also acts as the window manager.

## Call chains

Here are few call/usage chains of components in Sailfish OS from
ux/middleware to the hardware adaptation driver. The parts that mention
droid/libhybris/binder/Android HAL are dependant a bit on Android BSP
driver version of the device and for native adaptations the chain looks
different.

Should be noted that Sailfish OS does not have kernel provided with the
OS but kernel is something that is provided by the Hardware Adaptation
layer. Currently lowest supported kernel is 3.4 (which needs some
patches), and it is recommended to use kernel 4.4 or newer. There is
[configuration check
script](https://github.com/mer-hybris/mer-kernel-check%7Ckernel) that is
used to verify that kernel provides all required functionalities.

| |Area                                                                                                                                                                                                                                          | |Call chain                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | |Notes                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| Audio                                                                                                                                                                                                                                          | [pulseaudio](https://git.sailfishos.org/mer-core/pulseaudio/) \<\> [pulseaudio-modules-droid](https://github.com/mer-hybris/pulseaudio-modules-droid) \<\> [libhybris](https://github.com/mer-hybris/libhybris) \<\> [audioflingerglue](https://github.com/mer-hybris/audioflingerglue/) \<\> Android BSP libbinder \<\> miniaf \<\> Android BSP HAL: audio                                                                                                                      |                                                      |
| Bluetooth                                                                                                                                                                                                                                      | [Bluez5](https://git.sailfishos.org/mer-core/bluez5) \<\> kernel VHCI \<\> [bluebinder](https://github.com/mer-hybris/bluebinder) \<\> [libgbinder](https://github.com/mer-hybris/libgbinder/) \<\> Android BSP HAL: android.hardware.bluetooth                                                                                                                                                                                                                                  | Android BSP \>= 8                                    |
| Camera/Multimedia                                                                                                                                                                                                                              | [gst-droid](https://github.com/sailfishos/gst-droid/) \<\> [libhybris](https://github.com/mer-hybris/libhybris) \<\> [droidmedia](https://github.com/sailfishos/droidmedia/) \<\> Android BSP libbinder \<\> minimedia/minisf \<\> Android BSP HAL                                                                                                                                                                                                                               |                                                      |
| Display                                                                                                                                                                                                                                        | [mce](https://git.sailfishos.org/mer-core/mce) \<\> [mce-plugins-libhybris](https://github.com/mer-hybris/mce-plugin-libhybris/) \<\> [libhybris](https://github.com/mer-hybris/libhybris) \<\> Android BSP HAL: gralloc or hwcomposer                                                                                                                                                                                                                                           |                                                      |
| Fingerprint                                                                                                                                                                                                                                    | sailfish-fpd \<\> sailfish-fpd-slave \<\> [libgbinder](https://github.com/mer-hybris/libgbinder/) \<\> Android BSP HAL: android.hardware.fingerprint                                                                                                                                                                                                                                                                                                                             | Android BSP \>= 8                                    |
| Graphics                                                                                                                                                                                                                                       | [qtbase](https://github.com/mer-hybris/audioflingerglue/) \<\> [qt5-qpa-hwcomposer-plugin](https://github.com/mer-hybris/qt5-qpa-hwcomposer-plugin) \<\> libhybris-compat-library: libhwc2\_compat\_layer \<\> [libgbinder](https://github.com/mer-hybris/libgbinder/) \<\> Android BSP HAL: android.hardware.graphics.composer                                                                                                                                                  | Android BSP \>= 8                                    |
| [qtbase](https://github.com/mer-hybris/audioflingerglue/) \<\> [qt5-qpa-hwcomposer-plugin](https://github.com/mer-hybris/qt5-qpa-hwcomposer-plugin) \<\> [libhybris](https://github.com/mer-hybris/libhybris) \<\> Android BSP HAL: hwcomposer | Android BSP \<= 7                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                      |
| LED                                                                                                                                                                                                                                            | [mce](https://git.sailfishos.org/mer-core/mce) \<\> kernel                                                                                                                                                                                                                                                                                                                                                                                                                       |                                                      |
| [mce](https://git.sailfishos.org/mer-core/mce) \<\> [mce-plugins-libhybris](https://github.com/mer-hybris/mce-plugin-libhybris/) \<\> [libhybris](https://github.com/mer-hybris/libhybris) \<\> Android BSP HAL: lights                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                      |
| Location (GPS)                                                                                                                                                                                                                                 | [geoclue](https://github.com/mer-hybris/libgbinder/) \<\> [geoclue-providers-hybris](https://github.com/mer-hybris/geoclue-providers-hybris) \<\> [libgbinder](https://github.com/mer-hybris/libgbinder) \<\> Android BSP HAL: android.hardware.gnss                                                                                                                                                                                                                             | Android BSP \>= 8                                    |
| [geoclue](https://github.com/mer-hybris/libgbinder/) \<\> [geoclue-providers-hybris](https://github.com/mer-hybris/geoclue-providers-hybris) \<\> [libhybris](https://github.com/mer-hybris/libhybris) \<\> Android BSP HAL: gps               | Android BSP \<= 7                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                      |
| Modem                                                                                                                                                                                                                                          | [oFono](https://git.sailfishos.org/mer-core/ofono)([ril driver](https://git.sailfishos.org/mer-core/ofono/tree/master/ofono/drivers/ril)) \<\> [libgrilio](https://git.sailfishos.org/mer-core/libgrilio) \<\> [ofono-ril-binder-plugin](https://github.com/mer-hybris/ofono-ril-binder-plugin) \<\> [libgbinder-radio](https://github.com/mer-hybris/libgbinder-radio) \<\> [libgbinder](https://github.com/mer-hybris/libgbinder) \<\> Android BSP HAL: android.hardware.radio | Android BSP \>= 8                                    |
| [oFono](https://git.sailfishos.org/mer-core/ofono)([ril driver](https://git.sailfishos.org/mer-core/ofono/tree/master/ofono/drivers/ril)) \<\> [libgrilio](https://git.sailfishos.org/mer-core/libgrilio) \<\> socket \<\> Android BSP: rild   | Android BSP \<= 7                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                      |
| NFC                                                                                                                                                                                                                                            | [nfcd](https://git.sailfishos.org/mer-core/nfcd) \<\> [nfcd-binder-plugin](https://github.com/mer-hybris/nfcd-binder-plugin) \<\> [libgbinder](https://github.com/mer-hybris/libgbinder/) \<\> Android BSP HAL: android.hardware.nfc                                                                                                                                                                                                                                             | Android BSP \>= 8                                    |
| Sensors                                                                                                                                                                                                                                        | [sensorfw-qt5](https://git.sailfishos.org/mer-core/sensorfw/) \<\> [sensorfw-qt5-hybris](https://git.sailfishos.org/mer-core/sensorfw/) \<\> [libgbinder](https://github.com/mer-hybris/libgbinder/) \<\> Android BSP HAL: android.hardware.sensors                                                                                                                                                                                                                              | Android BSP \>= 8                                    |
| [sensorfw-qt5](https://git.sailfishos.org/mer-core/sensorfw/) \<\> [sensorfw-qt5-hybris](https://git.sailfishos.org/mer-core/sensorfw/) \<\> [libhybris](https://github.com/mer-hybris/libhybris) \<\> Android BSP HAL: sensors                | Android BSP \<= 7                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                      |
| Storage (eMMC & sdcard)                                                                                                                                                                                                                        | [udisks2](https://git.sailfishos.org/mer-core/usb-moded/) \<\> kernel                                                                                                                                                                                                                                                                                                                                                                                                            |                                                      |
| USB                                                                                                                                                                                                                                            | [usb\_moded](https://git.sailfishos.org/mer-core/usb-moded/) \<\> kernel                                                                                                                                                                                                                                                                                                                                                                                                         |                                                      |
| MTP                                                                                                                                                                                                                                            | [buteo-mtp](https://git.sailfishos.org/mer-core/buteo-mtp) \<\> [usb\_moded](https://git.sailfishos.org/mer-core/usb-moded/) \<\> kernel                                                                                                                                                                                                                                                                                                                                         | See [Architecture\#MTP](Architecture#MTP "wikilink") |
| WiFi                                                                                                                                                                                                                                           | [connman](https://git.sailfishos.org/mer-core/connman) ([sailfish\_wifi plugin](https://git.sailfishos.org/mer-core/connman/blob/master/connman/plugins/sailfish_wifi.c)) \<\> [libgsupplicant](https://git.sailfishos.org/mer-core/libgsupplicant) \<\> [wpa\_supplicant](https://git.sailfishos.org/mer-core/wpa_supplicant) \<\> kernel                                                                                                                                       |                                                      |
| Mobile data                                                                                                                                                                                                                                    | [connman](https://git.sailfishos.org/mer-core/connman) ([sailfish\_ofono plugin](https://git.sailfishos.org/mer-core/connman/blob/master/connman/plugins/sailfish_ofono.c)) \<\> [libgofono](https://git.sailfishos.org/mer-core/libgofono) \<\> [oFono](https://git.sailfishos.org/mer-core/ofono)                                                                                                                                                                              |                                                      |
| Volume keys                                                                                                                                                                                                                                    | [pulseaudio](https://git.sailfishos.org/mer-core/pulseaudio/) \<\> [lipstick](https://git.sailfishos.org/mer-core/lipstick/) \<\> [mce](https://git.sailfishos.org/mer-core/mce) \<\> kernel                                                                                                                                                                                                                                                                                     |                                                      |
| Power key                                                                                                                                                                                                                                      | call-ui or alarm-ui \<\> [mce](https://git.sailfishos.org/mer-core/mce) \<\> kernel                                                                                                                                                                                                                                                                                                                                                                                              | Short keypress                                       |
| [systemd](https://git.sailfishos.org/mer-core/systemd/) \<\> [dsme](https://git.sailfishos.org/mer-core/dsme/) \<\> kernel                                                                                                                     | 5s+ keypress                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                      |

For more information on the areas covered by middleware libraries and
services, see [Core Areas and APIs](/Reference/Core_Areas_and_APIs).

### MTP

usb-moded detects usb connection based on udev notification from kernel
and initiates gadget configuration and starts buteo-mtp. buteo-mtp then
finalizes the gadget configuration and handles data transmission.

## Key Architectural Areas

An overview of some architectural areas and the APIs which expose the
related functionality can be found in the page describing [Core Areas
and APIs](/Reference/Core_Areas_and_APIs) . Some more in-depth
documentation about key architectural areas follow:

  - [Cellular Telephony
    Architecture](/Reference/Core_Areas_and_APIs/Apps_and_MW/Telephony/Cellular_Telephony_Architecture) talks in
    detail about the mobile phone functionality
  - Audio Architecture describes audio routing and sharing
  - Screen display and application compositing is described in the
    Graphical Architecture
  - Multimedia Architecture covers the camera and video subsystems
  - The Qt Framework explains which Qt components applications should
    use to access features
  - Android compatibility is enabled by the Android Emulation Framework
