---
title: Target_Installation
permalink: Tools/Platform_SDK/Target_Installation/

---

**Attention: These instructions are only valid for Platform SDK versions
newer than or equal to 3.0.0. If you have an older Platform SDK, please
[upgrade it
first](/Tools/Platform_SDK/Installation).
If you are doing a fresh installation, please ignore this note.**  
  

## Platform SDK Targets and Toolings

The Platform SDK provides a chroot environment within which ScratchBox2
is available. ScratchBox2 uses qemu emulation to allow
architecture-specific binaries to be run on a host machine with a
different architecture. For example, it allows a user to run ARMv7
binaries on an x86 host.

Build tools specific to particular version of target operating system
are provided as a "tools distribution" (the terminology used in
ScratchBox2 documentation varies). In Sailfish OS Platform SDK this is
called "SDK tooling".

In order to meaningfully use ScratchBox2 to build software for Sailfish
OS devices, a target-architecture root filesystem (commonly known as an
"SDK rootfs" but again - the terminology varies) must be installed into
the Platform SDK chroot environment. This root filesystem contains build
dependencies (including binary executables and libraries) which are
needed to build software packages for the target device. It is the most
recognized part of a ScratchBox2 target configuration and so the terms
"rootfs" and "target" are often used interchangeably. In Sailfish OS
Platform SDK this is called "SDK target".

Whenever you enter a ScratchBox2 shell (via `sb2`), you must specify the
target which should be activated. Similarly, whenever you use the Mer
Build script (i.e. `mb2`) to build a package, you must specify the
target (which is then activated by ScratchBox2).

## Installing SDK Target and Tooling Tarballs

The latest public releases of Sailfish OS targets (and appropriate
toolings) are found here: <http://releases.sailfishos.org/sdk/targets/>

The SDK Assistant tool is available within the Platform SDK chroot
environment that simplifies the creation and deletion of ScratchBox2
targets. The most common use for the SDK Assistant tool is to create a
new SDK target:

`sdk-assistant create Sailfish OS-latest Sailfish_OS-latest-Sailfish_SDK_Tooling-i486.tar.7z`  
`sdk-assistant create Sailfish OS-latest-armv7hl Sailfish_OS-latest-Sailfish_SDK_Target-armv7hl.tar.7z`  
`sdk-assistant create Sailfish OS-latest-aarch64 Sailfish_OS-latest-Sailfish_SDK_Target-aarch64.tar.7z`  
`sdk-assistant create Sailfish OS-latest-i486 Sailfish_OS-latest-Sailfish_SDK_Target-i486.tar.7z`

You will always install SDK tooling before SDK targets that depends on
that tooling. Removal would be done in the opposite order. Note that
while SDK targets are target-cpu specific, SDK toolings are always i486
which is the only supported host platform.

You can also use a direct URL with this tool:

`sdk-assistant create Sailfish OS-latest `<http://releases.sailfishos.org/sdk/targets/Sailfish_OS-latest-Sailfish_SDK_Tooling-i486.tar.7z>  
`sdk-assistant create Sailfish OS-latest-armv7hl `<http://releases.sailfishos.org/sdk/targets/Sailfish_OS-latest-Sailfish_SDK_Target-armv7hl.tar.7z>  
`sdk-assistant create Sailfish OS-latest-aarch64 `<http://releases.sailfishos.org/sdk/targets/Sailfish_OS-latest-Sailfish_SDK_Target-aarch64.tar.7z>  
`sdk-assistant create Sailfish OS-latest-i486 `<http://releases.sailfishos.org/sdk/targets/Sailfish_OS-latest-Sailfish_SDK_Target-i486.tar.7z>

This will create three generic (i.e., hardware agnostic) SDK targets,
"Sailfish OS-latest-armv7hl" for ARMv7, "Sailfish OS-latest-aarch64" for
ARM64, and "Sailfish OS-latest-i486" for i486 platform. Their names are
to be used as an argument to `sb2`'s or `mb2`'s `-t` option. The single
created SDK tooling "Sailfish OS-latest" will be picked up automatically.

You can also use this tool for listing your installed toolings and
targets:

`sdk-assistant list`

And for removing them:

`sdk-assistant remove `<tooling-or-target-name>

It also supports updating a target and the tooling used by the target in
one step:

`sdk-assistant update `<target-name>

This is also the recommented way of updating SDK targets - it can save
you from some known issues with the upgrading process in special cases.

See `sdk-assistant --help` for more information.

## SDK Manager

The `sdk-manage` tool is also available within the Platform SDK chroot
environment, and allows the developer to manage installed SDK toolings
and targets in more detail.

With this tool it is possible to e.g. manually choose the SDK tooling or
the compiler toolchain that would be used for an SDK target:

`sdk-manage target install `<name>` `<url>` --tooling `<name>` --toolchain `<name>

It also allows to download and install an SDK target together with the
required tooling in one step:

`sdk-manage target install `<name>` `<url>` --tooling `<name>` --tooling-url `<url>

Concrete example:

`sdk-manage target install Sailfish OS-latest-armv7hl `<http://releases.sailfishos.org/sdk/targets/Sailfish_OS-latest-Sailfish_SDK_Target-armv7hl.tar.7z>` \`  
`     --tooling Sailfish OS-latest --tooling-url `<http://releases.sailfishos.org/sdk/targets/Sailfish_OS-latest-Sailfish_SDK_Tooling-i486.tar.7z>

See `sdk-manage --help` for more information.

## Separate Targets

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
