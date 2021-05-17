---
title: FAQ
permalink: Develop/Apps/FAQ/

---

## SDK Frequently Asked Questions

### How do I launch or shutdown the build engine or the emulator?

When you have a Sailfish OS project open in the IDE, you can see two
additional control icons in the left toolbar. Click on
![Application\_sdk\_faq-mersdk\_icon.png](Application_sdk_faq-mersdk_icon.png
"Application_sdk_faq-mersdk_icon.png") icon to start the build engine
and the
![Application\_sdk\_faq-emulator\_icon.png](Application_sdk_faq-emulator_icon.png
"Application_sdk_faq-emulator_icon.png") icon to start the emulator.
These buttons will also allow you to shut them down.

Control icon colour key:

  - Green – stopped, click to start
  - Gray – starting
  - Red – started, click to shut down

### How do I stop an application running in the emulator?

In the IDE editor view, at the lower edge, you can see a search box
followed by four tabs. Click on the **Application Output** tab. Click on
the red **Stop** button to stop the running application.

### How do I add additional development headers to the Sailfish OS target?

In the IDE,

1.  Go to **Options → Sailfish OS → Build Engine → Manage Build
    Targets...**
2.  Select build target from the list on top
3.  Choose **Manage packages** below, proceed to next page
4.  Enter search pattern(s) and click **Search packages** (read the tool
    tip of the search pattern field for more information)
5.  Select packages for installation and/or removal
6.  Repeat from step 4 if needed
7.  Proceed to next page to apply required changes

***With Sailfish SDK older than 3.0:***

The SDK control center provides options to extend the default Sailfish
OS target. In the IDE,

1.  Click on the **Sailfish OS** icon in the left toolbar to open the
    SDK control center.
2.  Click on the **manage** button next to the Sailfish OS-i486 target.
3.  The list of development headers available for install is displayed.
4.  Choose the package you wish to install and click on the **install**
    button next to it.

### How do I login into the emulator or build engine?

#### Emulator

For the purpose of opening a shell or running simple commands inside the
emulator, sfdk provides a convenient interface:

    $ sfdk emulator exec [<command> [<args>...]]

Using native SSH clients is possible too. The Emulator has a Developer
settings application, which you can use to set the password for the nemo
user. After that you can login to the emulator as user nemo.
Alternatively, you can login using the SSH keys.

    # as user nemo
    $ ssh -p 2223 nemo@localhost
    $ ssh -p 2223 -i ~/Sailfish OS/vmshare/ssh/private_keys/Sailfish_OS-Emulator-latest/nemo nemo@localhost
     
    # as root
    $ssh -p 2223 -i ~/Sailfish OS/vmshare/ssh/private_keys/Sailfish_OS-Emulator-latest/root root@localhost

**Note:** For connecting to other than the latest emulator, check Qt
Creator's Options under the Devices category, where you will find the
`SSH port` number and `SSH key` under the corresponding device, or use
`sfdk device list` on command line to retrieve the same information.

#### Build Engine

For the purpose of opening a shell or running simple commands inside the
build engine, sfdk provides a convenient interface:

    $ sfdk engine exec [<command> [<args>...]]

Using native SSH clients is possible too.

    # as user mersdk
    $ ssh -p 2222 -i ~/Sailfish OS/vmshare/ssh/private_keys/engine/mersdk mersdk@localhost
     
    # as root
    $ ssh -p 2222 -i ~/Sailfish OS/vmshare/ssh/private_keys/engine/root root@localhost

The SSH daemon (and other network services) on the virtual machines can
only be accessed from the host.

If you make any changes to the target on the build engine, be sure to
re-sync with the host using **Options → Sailfish OS → Build Engine →
Manage Build Targets... → Synchronize** from the IDE. (With Sailfish SDK
older than 3.0 use **Control Center → Targets → Sailfish OS-i486 → manage
→ sync**.)

### Why are you using virtual machines?

Using virtual machines allows us to efficiently deliver a consistent
build environment to a wide range of platforms. Whilst there is a small
performance penalty, we think this is a worthwhile tradeoff for the
benefits it gives us all. We have further optimisations planned.

### What are the shared folders for?

  - To securely share the SSH keys on the emulator and build engine.
  - So the build engine can see your code.
  - So Qt Creator can see the target in the build engine.

This essentially means that the "mersdk" user account in the build
engine is, as far as possible, your account. If you wish to share
additional directories then please discuss this with the community.

### Why is the emulator showing a black screen?

It thinks it is a real device and is saving power. We have a solution
planned for this. In the meantime a mouse movement will wake it up from
application or Home screen – if it is on the Lock screen you need to do
a big Pull down or emulate the Power button by pressing Host + ‘H’.

### I see scrollbars in the emulator window. How do I scale it to the window size?

Modern devices have a high vertical resolution which can be more than
some screens. The emulator uses a vertical resolution of 960 pixels and
allowance should be made for window borders too. In the VM menu select
**View→Scale** or press Host + ‘C’ to scale.

### Now I’ve built an awesome application – where do I share it?

The official place to share Sailfish OS applications is the [Jolla
Harbour](http://harbour.jolla.com/).

### I get the following error, it can’t create symlinks, what is the problem?

    ln -s libfoo.so.1.0.0 libfoo.so ln: creating symbolic link `libfoo.so.1':
    Protocol error make[1]: [libfoo.so.1.0.0] Error 1 (ignored)

This happens when `TARGET=library` is set in your library’s `.pro` file.
In Linux a library gets three additional symlinks:

    libfoo.so -> libfoo.so.1.0.0
    libfoo.so.1 -> libfoo.so.1.0.0
    libfoo.so.1.0 -> libfoo.so.1.0.0

Since the build location is on the shared home directory from Windows
which does not support symlinks, this error happens. You can work around
this problem by setting `TARGET=plugin`, then a non-versioned library
will be created during build time. If you want the symlinks in the RPM
file, you could create them in the `%install` section of your `.spec`
file like this:

    mv %{buildroot}/%{_libdir}/libfoo.so %{buildroot}/%{_libdir}/libfoo.so.1.0.0
    ln -s -t %{buildroot}/%{_libdir}/libfoo.so.1.0.0 %{buildroot}/%{_libdir}/libfoo.so
    ln -s -r %{buildroot}/%{_libdir}/libfoo.so.1.0.0 %{buildroot}/%{_libdir}/libfoo.so.1
    ln -s -r %{buildroot}/%{_libdir}/libfoo.so.1.0.0 %{buildroot}/%{_libdir}/libfoo.so.1.0

### How can I avoid issues with incompatible line endings?

It is recommended that text files under Sailfish OS projects use
Unix-style line endings by default and exceptions are done explicitly.

It helps a lot when the version control system is configured in a way
that other people get existing files checked out with the desired line
endings on all platforms. This is not the default usually. Git clients
are usually configured so that they do line endings conversion during
commit and check out operations. They maintain Unix-style line endings
in the repository and host-native line endings in the working tree. This
can be conveniently overriden at per-repository basis as in the
following example.

Store the following content in the '.gitattributes' file under the root
of the repository,

    # Use target-compatible line endings as the safe default for cross compilation.
    * text=auto eol=lf

add it to the index and renormalize existing files under repository.

    $ git add .gitattributes
    $ git add --renormalize .
    $ git commit -m 'Normalize line endings'

Finally renormalize the line endings under the working tree as well.

    $ git rm --cached -r .
    $ git reset --hard

Since now, Git will warn you when a file with other than Unix-style line
endings is added to the index.

    $ git add file-with-crlf.txt
    warning: CRLF will be replaced by LF in file-with-crlf.txt.
    The file will have its original line endings in your working directory

If this is intentional, attributes for the file should be explicitly
overriden in '.gitattributes'.

    * text=auto eol=lf
    file-with-crlf.txt text eol=crlf

If it was unintentional, then your text editor may need to be
reconfigured to use Unix-style line endings by default for newly created
files. Under Qt Creator it is **Options \> Text Editor \> Behavior \>
Default line endings**. (Requires SDK \>= 3.3)

SDK issues the following build time warning when files with CRLF line
endings are found under the project repository:

    Files with CRLF line endings found. Consult the Sailfish SDK FAQ to learn why to avoid that and how.

Should you need to continue using CRLF line endings for your project
files, it is sufficient that the RPM .spec and .yaml files use
Unix-style line endings in order to suppress that warning.

### Docker

#### What is the minimum Sailfish SDK version supporting the Docker-based build engine?

Sailfish SDK version 3.1 or later is required.

#### How can I set up Docker for use with Sailfish SDK?

Follow the generic instructions
[1](https://hub.docker.com/search/?type=edition&offering=community).

Linux users should also follow
[2](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user)
to ensure that Sailfish SDK can manage Docker as a non-root user.

Windows users should make sure that Docker is set up to use Linux
containers (instead of Windows containers).

#### I just upgraded my SDK, how can I switch to the Docker-based build engine?

Build engine selection is only possible during fresh Sailfish SDK
installation. You need to reinstall.

#### How does the Docker-based build engine compare on the performance side?

Build times with the Docker-based build engine are usually 30-40%
shorter than with the VirtualBox-based build engine both on Linux and
Windows. On Linux this also means that the build times achieved with the
Docker-based build engine are more or less equal to the build times
achieved with the (Linux-only) Platform SDK.

#### Is VirtualBox still a requirement with Docker-based build engine used?

When the Docker-based build engine is chosen, VirtualBox becomes an
optional dependency required by Sailfish OS emulators only. If you do
not use emulators, you may install Sailfish SDK where VirtualBox is not
available.

#### What are the compatibility issues with Sailfish OS emulators on Windows?

Docker on Windows relies on Hyper-V as a virtualization backend while
Sailfish OS emulators rely on VirtualBox. Until recently, it was not
possible to use Hyper-V simultaneously with other virtualization
technologies. Recent Windows and VirtualBox versions are said to remove
this limitation but the informations and user reports vary. There seems
to be no simple answer to the question whether the emulators will be
usable on your particular configuration when Docker is in use.

Hints:

  - Some sources mention Windows 10 1809 and VirtualBox 6.1.6 as the
    minimum versions
  - Some sources mention troubles to persist (or emerge) with newer
    versions
  - Try increasing the number of processors available to the emulator VM
    (sfdk emulator set vm.cpuCount=N). Try setting the maximum first

#### Is macOS support on the plan?

The main issue with VirtualBox-based build engine is the limited
performance of its file system sharing solution. Unfortunately the file
system sharing solution of Docker on macOS in not better in this respect
and so replacing VirtualBox with Docker would not make the expected
difference.

Recent versions of Docker Desktop for macOS come up with options to tune
the shared file IO performance at the cost of limited guarantees on
host-container file system consistency
([3](https://docs.docker.com/docker-for-mac/osxfs-caching/)). It needs
to be investigated yet if the implications are acceptable in our use
case.

#### Old sailfish-os-build-engine images keep piling up, is this desired?

This is a known issue with the initial Docker support (Sailfish SDK
3.1). With every build engine start/stop cycle, one new image layer is
created. This issue is likely going to be addressed with the next
Sailfish SDK release. Should you hit the limit of maximum 127 layers per
Docker image meanwhile, there are basically two options how to recover:

1.  Reinstall the Sailfish SDK (recommended)
2.  Flatten the history manually by following one of those guides
    available on the web, e.g.,
    [4](https://tuhrig.de/flatten-a-docker-container-or-image/) and
    taking care of restoring all the LABELs and the CMD set on the
    image.
