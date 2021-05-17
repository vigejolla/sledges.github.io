---
title: Networking
permalink: Reference/Core_Areas_and_APIs/Networking/

---

Networking capabilities are primarily implemented through:

  - ConnMan for general network connection management
  - oFono for cellular networking
  - BlueZ for Bluetooth connectivity
  - StateFS and MCE for system state management

## ConnMan

[ConnMan](https://01.org/connman) manages all internet connectivity
features on Sailfish OS. This includes:

  - Wi-Fi and cellular mobile data scanning and connections
  - WLAN hotspot connection sharing
  - Flight mode handling for disabling/restoring connectivity

The Sailfish OS adaptation of ConnMan is available at
<https://git.sailfishos.org/mer-core/connman>. Generally, Sailfish app
developers will find it easier to use
[libconnman-qt](https://git.sailfishos.org/mer-core/libconnman-qt)
instead, as that provides a Qt-based API as well as a QML module for
accessing ConnMan functionality.

## oFono

[oFono](https://01.org/ofono) is the base library used for all
cellular-related features. For example:

  - Cellular network registration and operator queries
  - Core modem management
  - Phone calls, SMS and MMS
  - Bluetooth connections for making calls via the Bluetooth Handsfree
    Profile (HFP)
  - SIM operations, including PIN and PUK codes and SIM ToolKit (STK)
    access
  - Supplementary service code handling including USSD/GSM Codes

The Sailfish OS adaptation of oFono is available at
<https://git.sailfishos.org/mer-core/ofono>. Generally, Sailfish app
developers will find it easier to use
[libqofono](https://git.sailfishos.org/mer-core/libqofono) and
[libqofonoext](https://git.sailfishos.org/mer-core/libqofonoext); these
provide Qt-based APIs and QML modules for accessing oFono functionality.

## Bluetooth

[BlueZ](http://www.bluez.org/) is the base library for all
Bluetooth-related features.

Currently, Sailfish OS provides the following profiles:

  - Audio Gateway for Headset Profile (HSP) and Handsfree Profile (HFP)
    for making calls via Bluetooth headsets
  - Advanced Audio Distribution Profile (A2DP) for playback of
    multimedia audio over a Bluetooth connection
  - SyncML client & server (SyncML) for synchronization of contact data
  - OBEX Object Push (OPP) for file exchange services
  - Phone Book Access Profile (PBAP) for exchanging phonebook data with
    a car kit

The Sailfish OS adaptation of BlueZ is available at
<https://git.sailfishos.org/mer-core/bluez>. Generally, Sailfish app
developers will find it easier to use
[libbluez-qt](https://git.sailfishos.org/mer-core/libbluez-qt) instead,
as that provides a Qt-based API and QML module for accessing BlueZ
functionality.

Bluetooth audio distribution is managed through
[PulseAudio](https://www.freedesktop.org/wiki/Software/PulseAudio/).

## StateFS and MCE

StateFS exposes the current system state (as reported by a variety of
plugins) via a synthetic filesystem, as namespaced properties. This
includes a variety of properties which affect networking, including the
cellular modem state, other connectivity states, and battery level. The
source code for StateFS can be found
[here](https://git.sailfishos.org/mer-core/statefs).

MCE provides mode-control for Sailfish OS. This includes management of
screen modes (on, dimmed, off, locked), power modes (including
deep-sleep and other low-power modes) and radio states which may affect
network connectivity or latency (for example, allowing network packet
I/O to be synchronised to a heartbeat timer to achieve power-saving
efficiencies). The source code for MCE can be found
[here](https://git.sailfishos.org/mer-core/mce/).
