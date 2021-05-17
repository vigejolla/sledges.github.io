---
title: Tools
permalink: Tools/

---

# Sailfish OS Tools

There are a number of key tools around Sailfish OS; most are used from
within one of the two primary SDKS: the Application SDK and the Platform
SDK. Hardware adaption work is done using the Hardware Adaptation
Development Kit.

## Application SDK

The Application SDK is based around Qt Creator and its tools and uses
virtual machine technology (VirtualBox) to provide an extremely portable
build system and a Sailfish OS emulator.

It consists of

  - Qt Creator
  - Mer/Sailfish OS plugins
  - Build Engine: A VM running the Platform SDK
  - Emulator: A VM running the Sailfish OS
  - Sailfish OS sb2 targets for ARM and x86 : headers and libraries
    needed to build Sailfish OS

Installing the Application SDK is covered in the [Application
Development](/Develop/Apps) area.

## Platform SDK

The Platform SDK is a command line environment. It consists of a minimal
Mer Core system with Mer Tools software repository enabled; this allows
you to install a variety of familiar linux tools and several more which
have been developed to make working with Sailfish OS easier. (As a point
of interest the same code found in the platform SDK is also used in
[OBS](/OBS), the automated build system.)

Read more about installing and using the [Platform
SDK](/Tools/Platform_SDK).

## HADK SDK

The Hardware Adaptation SDK consists of a Platform SDK and an Android
SDK built around a recommended Ubuntu installation. Details on this SDK
are found in the [Hardware Adaptation Development
Kit](/Tools/Hardware_Adaptation_Development_Kit).

## Development tools

A number of individual development tools are available such as:

  - scratchbox2 : a powerful cross-compilation suite
  - mb2 : a build assistant tool to create rpm packages and manage build
    dependencies
  - git : Sailfish OS uses git extensively for change control
  - mic : Local image generation tool

A more complete list including toolchain, analysis and testing tools can
be found in the [Development Tools](/Tools/Development_Tools) area.
