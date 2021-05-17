---
title: Image Creator
permalink: Services/Development/Image_Creator/

---

An Image Creator service builds system images for development, testing
and release. Images are built according to predefined lists of packages
and system files, as required for different system requirements, such as
different hardware, architecture or release purposes.

[Mer Imager](https://img.merproject.org) is an image creation service
that builds system images for Sailfish OS devices and SDK development.
It regularly assembles system images with a kernel and subsystem
integrated with middleware and application packages fetched from the Mer
[Open Build Service](/Services/Development/Open_Build_Service).

Images can be created using a default or custom list of package and
system requirements. These requirements will vary depending on the
target hardware architecture and filesystem, for example, or whether if
you are targeting a SDK environment system versus a full device image.
Also, the desired software packages may differ. For example:

  - When building an image for general development, it is useful to
    include a set of debugging and testing tools by default so that it
    is not necessary to install these later on during development;
    however, these tools are unnecessary for a release-type image.
  - For an image that is to be used in a demo-type capacity, you may
    want to include packages with dummy user content or predefined
    network configurations.
  - If you have a patched version of an existing system package and you
    want to test the effects of your changes on the system as a whole,
    you can use a default image build and then specify to include your
    custom upgraded package from your OBS home project.

To create a Mer image, go to the [Image creation
request](https://img.merproject.org/img/submit/) page. To view the list
of recently built (and currently building) images, see the [image
creation queue](https://img.merproject.org/img/queue/).
