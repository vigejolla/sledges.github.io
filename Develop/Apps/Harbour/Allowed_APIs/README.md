---
title: Allowed_APIs
permalink: Develop/Apps/Harbour/Allowed_APIs/

---

This information is valid as of Sailfish OS 4.0.1 release

You can always check the up-to-date list from the [validator config
files](https://github.com/sailfishos/sdk-harbour-rpmvalidator)

## Allowed Libraries

Your application can link against the following libraries:

### Qt 5 Core libraries

  - libQt5Core.so.5
  - libQt5Quick.so.5
  - libQt5Qml.so.5
  - libQt5Network.so.5
  - libQt5Gui.so.5

### Additional Qt 5 modules

  - libQt5Concurrent.so.5
  - libQt5Multimedia.so.5
  - libQt5Sql.so.5
  - libQt5Svg.so.5
  - libQt5XmlPatterns.so.5
  - libQt5Xml.so.5
  - libQt5DBus.so.5
  - libQt5WebKit.so.5
  - libQt5Sensors.so.5
  - libQt5Positioning.so.5
  - libQt5WebSockets.so.5

### Sailfish Silica library, Application Library + booster helper library

  - libsailfishapp.so.1
  - libmdeclarativecache5.so.0
  - libsailfishsilica.so.1

### Nemo Libraries

  - libnemonotifications-qt5.so.1
  - libnemothumbnailer-qt5.so.1
  - libkeepalive.so.1

### OpenGL ES 1.1, 2.0 and EGL

  - libEGL.so.1
  - libGLESv1\_CM.so.1
  - libGLESv2.so.2

### Standard system and C/C++ runtime libraries

  - ld-linux.so.2
  - ld-linux-armhf.so.3
  - ld-linux-aarch64.so.1
  - libpthread.so.0
  - libstdc++.so.6
  - libm.so.6
  - libgcc\_s.so.1
  - libc.so.6
  - librt.so.1
  - libdl.so.2
  - libz.so.1
  - libresolv.so.2

### Various additional libraries that are useful

  - libmlite5.so.0
  - libpng16.so.16
  - libdbus-1.so.3
  - libcurl.so.4
  - libfontconfig.so.1
  - libssl.so.1.1
  - libcrypto.so.1.1
  - liblzma.so.5
  - libxml2.so.2
  - libbz2.so.1
  - libexpat.so.1
  - libsqlite3.so.0

### GLib

  - libgio-2.0.so.0
  - libglib-2.0.so.0
  - libgmodule-2.0.so.0
  - libgobject-2.0.so.0
  - libgthread-2.0.so.0

### Low-level PulseAudio and Audio APIs

  - libpulse.so.0
  - libpulse-simple.so.0
  - libaudioresource.so.1

### Low-level Wayland Protocol APIs

  - libwayland-client.so.0
  - libwayland-cursor.so.0
  - libwayland-egl.so.1

### Multimedia

  - libogg.so.0
  - libvorbis.so.0
  - libvorbisenc.so.2
  - libvorbisfile.so.3
  - libsndfile.so.1

### SDL2

  - libSDL2-2.0.so.0
  - libSDL2\_gfx-1.0.so.0
  - libSDL2\_image-2.0.so.0
  - libSDL2\_mixer-2.0.so.0
  - libSDL2\_net-2.0.so.0
  - libSDL2\_ttf-2.0.so.0

## Allowed QML Imports

Your app is not allowed to have QML imports matching the following
patterns:

  - Bluetooth.\*
  - Meego.\*
  - Mer.\*
  - Nemo.\*
  - NemoMobile.\*
  - Sailfish.\*
  - Qt\*
  - org.nemomobile.\*
  - org.sailfishos.\*
  - com.jolla.\*
  - com.nokia.\*
  - com.meego.\*
  - org.kde.bluezqt

The exceptions to this rule are the following imports:

### Sailfish APIs

  - Sailfish.Silica 1.0
  - Sailfish.Pickers 1.0

### Nemo QML modules

  - Nemo.Notifications 1.0
  - Nemo.DBus 2.0
  - Nemo.Configuration 1.0
  - Nemo.Thumbnailer 1.0
  - Nemo.KeepAlive 1.2

### Qt APIs

  - QtQml 2.0, 2.1 and 2.2
  - QtQuick 2.0, 2.2, 2.3, 2.4, 2.5, 2.6
  - QtQuick.LocalStorage 2.0
  - QtQuick.XmlListModel 2.0
  - QtQuick.Particles 2.0
  - QtQuick.Window 2.0, 2.1 and 2.2
  - QtQuick.Layouts 1.0 and 1.1

### Additional QML modules

  - QtMultimedia 5.0, 5.1, 5.2, 5.3, 5.4, 5.5 and 5.6
  - QtWebKit 3.0
  - QtWebSockets 1.0 and 1.1
  - QtSensors 5.0, 5.1 and 5.2
  - QtGraphicalEffects 1.0
  - QtPositioning 5.2 and 5.4
  - QtQml.Models 2.1, 2.2 and 2.3
  - QtFeedback 5.0

### ContextKit

  - org.freedesktop.contextkit 1.0

### Python support

  - io.thp.pyotherside 1.0, 1.1, 1.2, 1.3, 1.4 and 1.5

## Allowed package dependencies

Usually you shouldn't add library depencencies or python module
dependencies to your package manually, as these dependencies are
generated automatically. Your rpm packages can require the following:

### Core libraries

  - libc.so.6
  - libpthread.so.0
  - librt.so.1
  - libm.so.6
  - libdl.so.2
  - ld-linux.so.2
  - ld-linux-armhf.so.3
  - ld-linux-aarch64.so.1
  - libz.so.1
  - libgcc\_s.so.1

### PulseAudio

  - libpulse.so.0
  - libpulse-simple.so.0

### C++ standard library

  - libstdc++.so.6

### libxml2

  - libxml2
  - libxml2.so.2

### Multimedia

  - libogg.so.0
  - libvorbis.so.0
  - libvorbisenc.so.2
  - libvorbisfile.so.3
  - libsndfile.so.1

### SDL2

  - libSDL2-2.0.so.0
  - libSDL2\_gfx-1.0.so.0
  - libSDL2\_image-2.0.so.0
  - libSDL2\_mixer-2.0.so.0
  - libSDL2\_net-2.0.so.0
  - libSDL2\_ttf-2.0.so.0

### Other libraries

  - libpng16.so.16
  - mlite-qt5
  - libcrypto.so.10
  - libcrypto.so.1.1
  - libssl.so.10
  - libssl.so.1.1
  - liblzma.so.5
  - libbz2.so.1
  - libexpat.so.1
  - libsqlite3.so.0

### Sailfish Silica QML API

  - sailfishsilica-qt5
  - libsailfishapp
  - mapplauncherd-booster-silica-qt5

### Nemo QML Imports

  - nemo-qml-plugin-notifications-qt5
  - nemo-qml-plugin-dbus-qt5
  - nemo-qml-plugin-configuration-qt5
  - nemo-qml-plugin-thumbnailer-qt5
  - nemo-qml-plugin-contextkit-qt5
  - qml(org.freedesktop.contextkit)
  - libkeepalive

### QML Imports

  - qt5-qtdeclarative-import-xmllistmodel
  - qt5-qtdeclarative-import-folderlistmodel
  - qt5-qtdeclarative-import-localstorageplugin
  - qt5-qtdeclarative-import-multimedia
  - qt5-qtdeclarative-import-websockets
  - qt5-qtqml-import-webkitplugin
  - qt5-qtdeclarative-import-particles2
  - qt5-qtdeclarative-qtquickparticles
  - qt5-qtsvg
  - qt5-qtgraphicaleffects
  - qt5-qtdeclarative-import-positioning
  - qt5-qtdeclarative-import-sensors
  - qt5-qtquickcontrols-layouts
  - qt5-qtdeclarative-import-models2
  - qt5-qtwebsockets

### Qt Modules

  - qt5-qtmultimedia
  - qt5-qtmultimedia-plugin-audio-pulseaudio
  - qt5-qtpositioning

### Image format plugins

  - qt5-plugin-imageformat-gif
  - qt5-plugin-imageformat-ico
  - qt5-plugin-imageformat-jpeg
  - qt5-qtsvg-plugin-imageformat-svg

### Python support

  - pyotherside-qml-plugin-python3-qt5

### Python modules

  - python3-gobject
  - python3-sqlite
  - python3dist(sqlite3)
  - python3dist(curses)
  - python3dist(attrs)
  - python3dist(pygobject)
  - python3dist(idna)
  - python3dist(lxml)
  - python3dist(pyopenssl)
  - python3dist(six)
  - python3dist(pyyaml)
  - python3dist(zope-interface)
  - python3dist(sortedcontainers)
  - python3dist(toml)
  - python3dist(twisted)

## Deprecated libraries

The following libraries have been deprecated, and they should no longer
be used in new code. They will be dropped from allowed libraries in a
future release:

### Deprecated in Sailfish OS 1.1.8

  - libpng15.so.15

### Deprecated in Sailfish OS 4.0.1

  - libssl.so.10
  - libcrypto.so.10

## Deprecated QML Imports

  - org.nemomobile.notifications 1.0
      - Renamed as 'Nemo.Notifications 1.0'
  - org.nemomobile.dbus 2.0
      - Renamed as 'Nemo.DBus 2.0'
  - org.nemomobile.configuration 1.0
      - Renamed as 'Nemo.Configuration 1.0'
  - org.nemomobile.thumbnailer 1.0
      - Renamed as 'Nemo.Thumbnailer 1.0'
