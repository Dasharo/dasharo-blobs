# Hardkernel ODROID H4 Blobs

The directory contains blobs to produce a full Dasharo firmware image for
Hardkernel ODROID H4+ platforms.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `me.bin` - Intel Management Engine
  * Version: v16.50.10.1351,
  * License:  [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.1,
  * License:  [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].
  * Changelog:
    * v1.1
      * Increased top swap size from 256KB to 512KB for Slim Bootloader
* `descriptor_netcard.bin` - Intel Flash Descriptor
  * Version: v1.1,
  * License:  [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].
  * Changelog:
    * v1.1
      * Increased top swap size from 256KB to 512KB for Slim Bootloader
    * v1.0
      * Based on `descriptor.bin` v1.0
      * Changed PCIe Controller 3 bifurcation to 4x1
      * Statically assign Flex I/O to PCIe for ports 11 and 12

Intel Management Engine and Flash Descriptor have been generated with Intel
CSME for Alder Lake-N v16.50.10.1351 software kit using genuine components
provided by Intel, subject to the [PV Intel OBL Software License Agreement
11.2.2017][INTEL SLA].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on
[3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack). Current signing key:
[Dasharo release 0.x compatible with Hardkernel ODROID H4 family signing
key][KEY]

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/dasharo/hardkernel_odroid_h4/dasharo-release-0.x-compatible-with-hardkernel-odroid-h4-family-signing-key.asc