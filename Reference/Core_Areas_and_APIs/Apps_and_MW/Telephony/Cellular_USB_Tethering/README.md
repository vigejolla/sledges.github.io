---
title: Cellular USB Tethering
permalink: Reference/Core_Areas_and_APIs/Apps_and_MW/Telephony/Cellular_USB_Tethering/

---

Cellular USB Tethering is a part of the [Cellular Telephony
Architecture](/Reference/Core_Areas_and_APIs/Apps_and_MW/Telephony/Cellular_Telephony_Architecture)

## Cellular USB Tethering

usb\_moded is a daemon that activates a USB (Universal Serial Bus)
profile based on the USB cable connection status that it tracks.

It uses a D-Bus system bus for all the system wide communications. Among
other functionality usb\_moded can set up USB tethering, ie: it can
share the data connection of the device with another device.A typical
case of this is a laptop using a mobile phone for connecting to the
Internet. When a cellular network is used to access the Internet, oFono
is used to check if the device is roaming, and if so, if roaming is
allowed. (Roaming means using the cellular connection outside the home
subscription network.)
