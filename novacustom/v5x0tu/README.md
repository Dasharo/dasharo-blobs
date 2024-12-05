# NovaCustom V5x0TU

The directory contains blobs to produce a full Dasharo firmware image
for Novacustom V540TU/V560TU laptops.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `me.bin` - Intel Management Engine
  * Version: v18.0.5.2040
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.0
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `gbe.bin` - Intel Gigabit Ethernet NVM binary for Meteor Lake-P/M Corporate
  * Version: v1.1
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `MeteorLakeFspBinPkg` - Intel Firmware Support Package for Meteor Lake from
  MTL_BIOS_4122_12 software kit provided by Intel
  * Version: 2024/04/30 v4122
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `IntelGopDriver.efi` - Intel Graphics Output Protocol UEFI driver
  * Version: v22.0.1041
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]

Intel Management Engine and Flash Descriptor have been generated from Intel
CSME for Meteor Lake H/U 18.0.5.2040v2 Consumer software kit using genuine
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
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/customer-keys/novacustom/dasharo-release-0.9.x-for-novacustom-signing-key.asc
