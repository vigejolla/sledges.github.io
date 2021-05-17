---
title: Flashing
permalink: Develop/HW_Adaptation/Flashing/

---

Flashing is the process of copying the entire OS to a device's internal
storage.

It's generally carried out over a USB connection using tools like adb
and fastboot although it can be done "over the air" (OTA)

The internal storage is split into a number of partitions each (or many)
of which contains one of the following:

  - bootloader
  - kernel
  - firmware
  - system filesytem
  - data filesystem
  - recovery filesystem
  - other filesystems
  - backups of any of the above

There are both development tools such as the recovery system,
[fastboot](/Develop/L10n/Style_Guides/fastboot and [adb](adb) as well as
on-device user-level applications such as the system updater which are
capable of writing to these partitions.

For more details about flashing for developers please see the [Hardware
Adaptation Development
Kit](/Tools/Hardware_Adaptation_Development_Kit).
