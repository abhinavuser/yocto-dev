# Yocto Project - meta raspberrypi

Yocto BSP layer for the Raspberry Pi boards - <http://www.raspberrypi.org/>

Cloned Version configured for 4B board

## Quick links

* Git repository web frontend:
  <https://github.com/agherzan/meta-raspberrypi>
* Mailing list (yocto mailing list): <yocto@lists.yoctoproject.org>
* Issues management (Github Issues):
  <https://github.com/agherzan/meta-raspberrypi/issues>
* Documentation: <http://meta-raspberrypi.readthedocs.io/en/latest/>

## Description

This is the general hardware specific BSP overlay for the RaspberryPi device.

More information can be found at: <http://www.raspberrypi.org/> (Official Site)

The core BSP part of meta-raspberrypi should work with different
OpenEmbedded/Yocto distributions and layer stacks, such as:

* Distro-less (only with OE-Core).
* Yoe Disto (Video and Camera Products).
* Yocto/Poky (main focus of testing).

## Yocto Project Compatible Layer

This layer is officially approved as part of the `Yocto Project Compatible
Layers Program`. You can find details of that on the official Yocto Project
[website](https://www.yoctoproject.org/development/yocto-project-compatible-layers/).

## Dependencies

This layer depends on:
* URI: https://git.openembedded.org/bitbake
  * branch: master
  * revision: HEAD

* URI: https://git.openembedded.org/openembedded-core
  * branch: master
  * revision: HEAD

* URI: https://git.yoctoproject.org/meta-yocto
  * branch: master
  * revision: HEAD

## Quick Start

1. source openembedded-core/oe-init-build-env rpi-build
2. Add this layer to bblayers.conf and the dependencies above
3. Set MACHINE in local.conf to one of the supported boards
4. bitbake core-image-base
5. Use bmaptool to copy the generated .wic.bz2 file to the SD card
6. Boot your RPI

## Quick Start with kas

1. Install kas build tool from PyPi (sudo pip3 install kas)
2. Set the `machine: ` in kas-poky-rpi.yml to one of the supported boards (see conf/machine/*.conf)
3. kas build meta-raspberrypi/kas-poky-rpi.yml
4. Use bmaptool to copy the generated .wic.bz2 file to the SD card
5. Boot your RPI

To adjust the build configuration with specific options (I2C, SPI, ...), simply add
a section as follows:

```
local_conf_header:
  rpi-specific: |
    ENABLE_I2C = "1"
    RPI_EXTRA_CONFIG = "dtoverlay=disable-bt"
```

To configure the machine, you have to update the `machine` variable.
And the same for the `distro`.

For further information, you can read more at <https://kas.readthedocs.io/en/latest/index.html>

## Contributing

You can send patches using the GitHub pull request process or/and through the
Yocto mailing list. Refer to the
[documentation](https://meta-raspberrypi.readthedocs.io/en/latest/contributing.html)
for more information.
