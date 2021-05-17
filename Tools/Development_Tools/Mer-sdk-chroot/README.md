---
title: Mer-sdk-chroot
permalink: Tools/Development_Tools/Mer-sdk-chroot/

---

`   usage: /srv/mer/sdks/sfossdk/mer-sdk-chroot [-u `<user>`] [-m <all|none|root|home>] [-r `<SDK root path>`] [`<command>` `<args>` ..]`  
`          /srv/mer/sdks/sfossdk/mer-sdk-chroot -h`  
  
`      This is the Mer chroot SDK.`  
`      For information see `<http://wiki.merproject.org/wiki/Platform_SDK>  
  
`     If command is not present,`  
`        used to enter the SDK and begin working. The SDK bash shell is a`  
`        login shell. See below for .profile handling`  
`        Must be preceded by a 'mount' to setup the SDK.`  
`        May be used in multiple terminals and simply enters the`  
`        chroot`  
  
`     If command is present,`  
`        used to execute an arbitrary command from within the SDK chroot`  
`        environment. The environment variable MERSDK is set to 1 to allow`  
`        SDK detection.`  
  
`     Options:`  
  
`      -u  System user to link into SDK (not needed if using sudo)`  
`      -m  Devices to bind mount from host: none, all (default)`  
`          root, home`  
`      -r The root of the SDK to use - normally derived from the`  
`         pathname of /srv/mer/sdks/sfossdk/mer-sdk-chroot`  
`      -h  Show this help`  
  
`     Profile`  
  
`     Entering the SDK runs the user's normal .profile and any (SDK)`  
`     system profile entries. It will not execute the host's system`  
`     profile entries.`  
  
`     The environment variable MERSDK is set to 1 to allow .profile to`  
`     detect the SDK.`  
  
`     If the user has a ~/.mersdk.profile then it is sourced after the`  
`     normal .profile handling (this allows the common use case of`  
`     setting a profile to be handled).`  
  
`     Hooks`  
  
`     If the user specified has a .mersdkrc in their /root, it will be`  
`     sourced to allow hook functions to be defined. Hooks are run as`  
`     root. No commands should be executed immediately.`  
  
`     These hooks are usually used to define symbolic links from any`  
`     /parentroot/data type filesystems into the SDK root to setup`  
`     system specific shared caches or filesystem layouts etc`
