---
title: Installation_Before_2.1.3
permalink: Tools/Platform_SDK/Installation_Before_2.1.3/

---

**Attention: These instructions are only valid for Platform SDK versions
older than 2.1.3.**  
  
The Sailfish OS platform SDK contains [Development
Tools](/Tools/Development_Tools) like Scratchbox2, [ MIC (Image
Creation)](/Image_Creation),
[Spectacle](/Spectacle), osc, qemu, etc, to make it easier for
a developer to work with Sailfish OS.

# Quick start

If you're in a hurry then this should get you going (if it doesn't work
then read the full instructions carefully\!) :

`  `  
`export PLATFORM_SDK_ROOT=/srv/mer`  
`curl -k -O http://releases.sailfishos.org/sdk/installers/latest/Jolla-latest-Sailfish OS_Platform_SDK_Chroot-i486.tar.bz2 ;`  
`sudo mkdir -p $PLATFORM_SDK_ROOT/sdks/sfossdk ;`  
`sudo tar --numeric-owner -p -xjf Jolla-latest-Sailfish OS_Platform_SDK_Chroot-i486.tar.bz2 -C $PLATFORM_SDK_ROOT/sdks/sfossdk  ;`  
`echo "export PLATFORM_SDK_ROOT=$PLATFORM_SDK_ROOT" >> ~/.bashrc`  
`echo 'alias sfossdk=$PLATFORM_SDK_ROOT/sdks/sfossdk/mer-sdk-chroot' >> ~/.bashrc ; exec bash ;`  
`echo 'PS1="PlatformSDK $PS1"' > ~/.mersdk.profile ;`  
`echo '[ -d /etc/bash_completion.d ] && for i in /etc/bash_completion.d/*;do . $i;done'  >> ~/.mersdk.profile ;`  
`sfossdk`

Once you've installed the Platform SDK you'll need to [installation a
Platform SDK
Target](/Tools/Platform_SDK/Target_Installation_Before_2.1.3).

It's recommended that you read sections below for pre-requisites,
options and details on installing extra architecture toolchains, tools
etc.

# Platform SDK

The default download contains:

  - Development tools
  - Image creation tools
  - OBS development tools
  - ARMv7hl toolchain

You can also install :

  - Cross-build tools for x86, armv7hl
  - Debugging tools
  - Testing tools
  - Python development
  - Ruby development

# Installing the Platform SDK

## SDK Requirements

The Platform SDK will run on most modern Linux machines. It needs:

  - Linux distribution (one in a virtual machine works well), running
    2.6.37 or newer kernel
  - about 400Mb free space to install
  - The SDK must be installed on a standard filesystem and "nosuid" must
    not be set. (Note: [recent
    ecryptfs](http://askubuntu.com/questions/210048/error-when-running-binary-with-root-setuid-under-encrypted-home-directory)
    will automatically use and enforce nosuid. Automounted usb drives
    typically have "nosuid" set too.)
  - hundreds of Mb for rpm caches for osc and mic as well as for SB2
    targets
  - Generic x86 CPU
  - user must have sudo rights

## Installation / setup

The Platform SDK is provided as a rootfs tarball that contains essential
tools for Sailfish OS platform development along with a helper script to
enter the rootfs.

Filesystem requirements:

  - The Platform SDK can be installed to any location with enough space
    - we'll use /srv/ as per the [Linux
    FHS](http://www.pathname.com/fhs/pub/fhs-2.3.html#SRVDATAFORSERVICESPROVIDEDBYSYSTEM)
    (feel free to adapt the commands to use any other location).
  - The installation path must contain an intermediate directory called
    'sdks' which only has Platform SDKs inside. eg
    /srv/mer/sdks/sfossdk/...

To setup the Platform SDK:

  - Download the latest stable Platform SDK rootfs tarball with the
    common armv7hl toolchain preinstalled:

`curl -k -O `<http://releases.sailfishos.org/sdk/installers/latest/Jolla-latest-Sailfish OS_Platform_SDK_Chroot-i486.tar.bz2>` `

  - Optionally, you can check the release notes from the [Application
    SDK Release Notes](/Application_SDK#Release_Notes). The
    SDK Build Engine section also contains the latest changes to the
    Platform SDK.

<!-- end list -->

  - Create a directory for the Platform SDK rootfs and extract the
    tarball as root or with sudo:

`sudo mkdir -p /srv/mer/sdks/sfossdk`  
`sudo tar --numeric-owner -p -xjf Jolla-latest-Sailfish OS_Platform_SDK_Chroot-i486.tar.bz2 -C /srv/mer/sdks/sfossdk`

## Platform SDK control script

The Platform SDK rootfs contains a helper script to enter the chroot
named 'mer-sdk-chroot'. The helper script is located in the root
directory (/) of the rootfs. It requires you to have sudo ability.

As mentioned, the Platform SDK is location independent so it uses the
location of the helper script to determine which Platform SDK to enter.

## Entering Platform SDK

Before entering the Platform SDK you may want to make an Platform SDK
equivalent of ".profile" to give you a nice prompt to remind you that
you are in the Platform SDK. This also reads the bash autocompletion
scripts from inside the chroot.

`cat << EOF >> ~/.mersdk.profile`  
`PS1="PlatformSDK \$PS1"`  
`if [ -d /etc/bash_completion.d ]; then`  
`   for i in /etc/bash_completion.d/*;`  
`   do`  
`      . \$i`  
`   done`  
`fi`  
`EOF`

To enter the Platform SDK rootfs with the helper script run

    /srv/mer/sdks/sfossdk/mer-sdk-chroot

You should find that you are operating under your normal username and
that your home directory is available as `/home/`<username> and any
other mountpoints are mounted under `/parentroot/*`

You have sudo rights automatically. If sudo fails within the sdk, make
sure that the filesystem the sdk is on is not mounted with the "nosuid"
parameter. "mount" on the host system gives you this information, add
"suid" as parameter in fstab, if necessary.

## Useful Alias

If you tend to use a single instance of the Platform SDK then this alias
is useful

` echo alias sfossdk=/srv/mer/sdks/sfossdk/mer-sdk-chroot >> ~/.bashrc ; exec bash`

## Basic tasks

### Compiling with the Platform SDK

Platform SDK can be used to compile code as well, e.g., you can compile
simple applications within the Platform SDK:

`mkdir ~/src`  
`cat <`<EOF >`~/src/hello.c`  
`#include <stdio.h>`  
`int main(int argc, char **argv)`  
`{`  
`   printf("Hello World\n");`  
`   return 0;`  
`}`  
`EOF`  
`gcc ~/src/hello.c -o ~/src/hello`

and run it:

`~/src/hello`

Note that this compilation is strictly for compiling code for use in the
Platform SDK itself - i.e. it's not terribly useful for writing code for
Sailfish OS devices; for that you need a suitable Target ... keep
reading.

# Next Steps

The next step is to look at [setting up the Platform SDK
Targets](/Tools/Platform_SDK/Target_Installation) and installing and
using more [Development Tools](/Tools/Development_Tools)

# Updating the Platform SDK

The general rule is that the SDK release version should match the target
release version. You can check your current release version by executing
`ssu re` in the SDK. For a newer SDK release version check out the
[Application SDK Release
Notes](/Application_SDK#Release_Notes). In this example we
will use Jolla release `2.0.2.48`.

If you want to update the Platform SDK, you should first update your
installed target(s), e.g.:

``` 
 sb2 -t example-target -m sdk-install -R
 ssu re 2.0.2.48
 zypper ref
 zypper dup
 exit
```

And then you can update the actual Platform SDK:

``` 
 sudo ssu re 2.0.2.48
 sudo zypper ref
 sudo zypper dup
```

# Removing the Platform SDK

Simply exit all chroot instances and, using sudo, remove
`/srv/mers/sdks/sfossdk`.

# Extras

## Multiple Platform SDKs

You should be able to install and connect to multiple Platform SDKs at
the same time.

## Known Issues

### work around bug \#554 : mic failure

To work around a [bug
\#554](https://bugs.merproject.org/show_bug.cgi?id=554) add the
following to `~/.mersdk.profile` (e.g. Fedora \>= 17 needs that):

`export PATH=$PATH:/sbin`

### "not enough disk space left" or similar

If you do actually have enough disk then the problem is possible that
the kernel on your host is too old. To run Platform SDK you should be
running kernel 2.6.37 or newer on your host.
