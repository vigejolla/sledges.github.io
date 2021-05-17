---
title: Telephony
permalink: Reference/Core_Areas_and_APIs/Apps_and_MW/Telephony/

---

### Telephony

The Sailfish OS telephony features include the capabilities for making
phone calls, alerting with ringtones, phone call audio routing, SIM
management and dual SIM capabilities, GPRS and phone network operator
connections, AT command handling, SIM ToolKit interaction and general
modem management.

### Relevant development repositories

The oFono framework is used for general modem management, and ConnMan
for network connection management:

  - [ofono](https://git.sailfishos.org/mer-core/ofono) - Jolla fork of
    <https://01.org/ofono>
  - [libqofono](https://git.sailfishos.org/mer-core/libqofono) - A Qt
    library for accessing the ofono daemon, including a QML API
  - [libqofonoext](https://git.sailfishos.org/mer-core/libqofonoext) - A
    Qt library for accessing nemomobile-specific ofono extensions,
    including a QML API
  - [connman](https://git.sailfishos.org/mer-core/connman) - Jolla fork
    of <https://01.org/connman>
  - [libconnman-qt](https://git.sailfishos.org/mer-core/libconnman-qt) -
    A Qt library for accessing connman, including a QML API

Phone calls are managed through oFono and Telepathy. In addition, the
middleware voicecall packages implement plugins to use telepathy with
ofono and activate calls, and libcommhistory collects a history of phone
calls and messages for later lookup:

  - [telepathy-ring](https://git.sailfishos.org/mer-core/telepathy-ring)
    - Telepathy connection manager for GSM and similar mobile telephony
  - [telepathy-qt](https://git.sailfishos.org/mer-core/telepathy-qt) -
    Qt library for telepathy clients
  - [telepathy-mission-control](https://git.sailfishos.org/mer-core/telepathy-mission-control)
    - account manager and channel dispatcher for Telepathy
  - [mer-core/voicecall](https://git.sailfishos.org/mer-core/voicecall)
    - voicecall and voicecallmanager for implementing dialer UIs and
    activating calls
  - [libcommhistory](https://git.sailfishos.org/mer-core/libcommhistory)
    - central management and collection of call and messaging events

Call audio management and routing is implemented through PulseAudio:

  - [pulseaudio](https://git.sailfishos.org/mer-core/pulseaudio)
  - [pulseaudio-modules-nemo](https://git.sailfishos.org/mer-core/pulseaudio-modules-nemo)

### Architecture

See [Cellular Telephony
Architecture](/Reference/Core_Areas_and_APIs/Apps_and_MW/Telephony/Cellular_Telephony_Architecture).
