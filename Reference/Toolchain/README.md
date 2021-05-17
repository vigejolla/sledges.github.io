---
title: Toolchain
permalink: Reference/Toolchain/

---

## Platform SDK Toolchain

Sailfish OS is based upon Mer and uses the Mer toolchain, as provided by
the [Platform SDK](/Tools/Platform_SDK).

### Build Tools

The toolchain consists of Linaro GCC, the GNU ld linker and GNU libc,
run within a ScratchBox2 virtual machine within the Mer SDK chroot. As
described in the Platform SDK documentation, a single Mer SDK
installation can include multiple SDK Targets. Any particular SDK Target
is used to perform builds for a specific architecture (e.g., armv7,
i586, etc). You can check to see which version of the build tools are
installed for a given architecture by checking the version of the
cross-\[arch\]-gcc and cross-\[arch\]-binutils packages, within a Mer
SDK chroot prompt.

For example:

`    # enter the Mer SDK chroot`  
`    $ /srv/mer/sdks/sdk/mer-sdk-chroot`  
`    # check the installed version of the cross-armv7hl-gcc package`  
`    [MerSDK] $ sudo zypper info cross-armv7hl-gcc`

It is this version of GCC which will be available within an sdk-build
mode ScratchBox2 prompt within an armv7hl SDK target.

For example:

`    # enter the Mer SDK chroot`  
`    $ /srv/mer/sdks/sdk/mer-sdk-chroot`  
`    # enter the SB2 target in sdk-build mode, assumes that the target already exists`  
`    [MerSDK] $ sb2 -t sfos-armv7hl -m sdk-build`  
`    # check which version of gcc is used when building with this target`  
`    [SB2 sdk-build sfos-armv7hl] gcc -v`

Note that to build packages, usually the ScratchBox2 prompt is not
usually necessary, as the `mb2` script performs the necessary steps to
build and package a project for the developer.

### Other Tools

The Mer SDK chroot includes tools like `mic` for image creation and
`osc` for OBS integration.

## Android BSP Support

Sailfish OS utilises [libhybris](https://github.com/libhybris) to
leverage existing Android board support packages and allow using
libraries and binary-only device drivers built with the Android
toolchain to be used within Sailfish OS.
