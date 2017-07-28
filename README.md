# Overview

epipyimg is part of Epipylon -- http://www.epipylon.com/

epipyimg provides the tools necessary to build Epipylon SD card images.

In most cases, the epipyimg tools will pull packages from the Epipylon
package repository at packages.epipylon.com.  If you want to install
custom packages which are unavailable from the Epipylon repository, you
may set up a custom repository using the Debian tool 'reprepro'.

# Contents

epipyimg contains the following components:

* `bin/` - Various tools used in image production
* `bin/img-full-build` - From scratch, build a new Epipylon image
* `bin/img-cp` - Copy a completed Epipylon image to an SD card
* `bin/img-mount` - Mount the image at `img/disk.img` onto `root/`
* `bin/img-umount` - Unmount the image mounted at `root/`

# Building

Building Epipylon images requires a few tools from Debian and QEMU 
ARM binary emulation.  On Fedora, these tools can be installed with:

    sudo dnf install dpkg debootstrap qemu-user-static

A development image can be built with:

    sudo bin/img-full-build devel

A completed image can then be copied to an SD card:

    #  Replace XXXX with the build image timestamp and YY with the SD card
    dd if=img/epipylon-devel-XXXX.img of=/dev/sdYY bs=4M status=progress

# License

epipyimg is licensed under the GNU General Public License 2.0.
