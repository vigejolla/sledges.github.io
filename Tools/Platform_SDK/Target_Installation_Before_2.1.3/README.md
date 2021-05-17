---
title: Target_Installation_Before_2.1.3
permalink: Tools/Platform_SDK/Target_Installation_Before_2.1.3/

---

**Attention: These instructions are only valid for Platform SDK versions
older than 2.1.3.**  
  

## Platform SDK Target

The Platform SDK provides a chroot environment within which ScratchBox2
is available. ScratchBox2 uses qemu emulation to allow
architecture-specific binaries to be run on a host machine with a
different architecture. For example, it allows a user to run ARMv7
binaries on an x86 host.

In order to meaningfully use ScratchBox2 to build software for Sailfish
OS devices, a target-architecture root filesystem (commonly known as an
"SDK rootfs") must be installed into the Platform SDK chroot
environment. This root filesystem contains binaries (including
executables and libraries) which are needed to build software packages
for the target device.

Whenever you enter a ScratchBox2 shell (via `sb2`), you must specify the
target rootfs which should be activated. Similarly, whenever you use the
Mer Build script (i.e. `mb2`) to build a package, you must specify a
target rootfs (which is then activated by ScratchBox2). When creating
the SDK target, you must specify both a name and an architecture
toolchain, as well as the SDK rootfs tarball from which the target
should be created.

### SDK Target Root FS Tarballs

The latest public releases of Sailfish OS Targets are found here:
<http://releases.sailfishos.org/sdk/latest/targets/targets.json>

Before installing the actual target you need to install the cross
compilation tools that are for your target architecture, e.g.,

`PLATFORM_SDK $`  
  
`sudo zypper in -t pattern Mer-SB2-armv7hl`

### SDK Assistant

The SDK Assistant tool is available within the Platform SDK chroot
environment. It simplifies the creation and deletion of target-specific
SDK rootfs instances. The most common use for the SDK Assistant tool is
to create a new SDK target from a rootfs tarball. For example, to create
a new ARMv7 Sailfish OS SDK target, the following command can be issued:

`sdk-assistant create Sailfish OS-armv7hl Jolla-latest-Sailfish_SDK_Target-armv7hl.tar.bz2`

You can also use a direct URL with this tool:

`sdk-assistant create Sailfish OS-armv7hl `<http://releases.sailfishos.org/sdk/latest/Jolla-latest-Sailfish_SDK_Target-armv7hl.tar.bz2>

This will create a generic (i.e., hardware agnostic) ARMv7 rootfs SDK
target called "Sailfish OS-armv7hl" (which can be used to build ARMv7
binaries using mb2 or sb2), from the SDK rootfs tarball specified.

You can also use this tool for listing your installed targets:

`sdk-assistant list`

And for removing them:

`sdk-assistant remove `<target-name>

### SDK Target Manager

The `sdk-manage` tool is also available within the Platform SDK chroot
environment, and allows the developer to manage installed toolchains and
SDK targets in more detail.

Toolchains provide ScratchBox2 configurations, QEMU, GCC and binutils
for given architecture. To list the currently installed toolchains, do:

`sdk-manage --toolchain --list`

If the toolchain is present then the name will be followed by an 'i' to
indicate that it is installed.

If it is not present then issue the command:

`sdk-manage --toolchain --install TOOLCHAIN-NAME`

To install a new SDK target use:

` sdk-manage --target --install <name> <toolchain> <url> `

For example:

` sdk-manage --target --install Sailfish OS-armv7hl Mer-SB2-armv7hl http://releases.sailfishos.org/sdk/latest/Jolla-latest-Sailfish_SDK_Target-armv7hl.tar.bz2 `

This will install a new SDK target named "Sailfish OS-armv7hl" using the
Mer-SB2-armv7hl toolchain, from the given SDK rootfs tarball.

Note: The tools used to install targets are not yet finalised and care
is needed when using them. The `sdk-manage` tool is primarily intended
to be used inside the Platform SDK and not as a standalone tool.

Note: Older versions of `sdk-manage` need also `--use-chroot-as $(id
-un)`.

### Separate Targets

It is often useful to have separate targets for different devices as
well as for different architectures, in case some particular package you
are building requires low-level, hardware specific packages. An example
of this is Hybris-related components. In general, these have to be built
against hardware-specific libraries, and so for these it is usually best
to create a separate, device-specific target to build your package in.

In most SDK targets, hardware agnostic libraries are provided where
possible. For example, Mesa3D libraries provide the OpenGL symbols to
avoid requiring hardware-specific libraries to be installed into a
generic ARMv7 arch SDK target.
