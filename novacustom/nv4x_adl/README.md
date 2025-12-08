# Novacustom NV4xPZ blobs

The directory contains blobs to produce a full Dasharo firmware image
for Novacustom NV4xPZ laptops.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `me.bin` - Intel Management Engine
  * Version: v16.1.40.2765,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Changelog:
    * v16.1.40.2765:
      * generated from Intel CSME Alder Lake-P 16.1.40.2765v3
    * v16.1.30.2307:
      * generated from Intel CSME for Raptor Lake-P 16.1.30.2307v4
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.1,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Changelog:
    * Version: v1.1:
      * generated from Intel CSME Alder Lake-P 16.1.40.2765v3
    * Version: v1.0:
      * generated from Intel CSME for Raptor Lake-P 16.1.30.2307v4
* `IntelGopDriver.efi` - Intel GOP Driver
  * Version: v21.0.1066,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]

Intel Management Engine and Flash Descriptor have been generated from Intel
CSME for Alder Lake-P 16.1.40.2765v3 Consumer software kit using genuine
components provided by Intel, subject to the
[PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on [3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack).
Current signing key:
[Novacustom Open Source Firmware Release 1.x Signing Key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/customer-keys/novacustom/novacustom-open-source-firmware-release-1.x-key.asc
