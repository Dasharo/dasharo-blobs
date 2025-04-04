# Protectli VP3210/VP3230 blobs

The directory contains blobs to produce a full Dasharo firmware image
for Protectli VP3210/VP3230 and VP2430 platforms.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `vp32xx/`
  * `me.bin` - Intel Management Engine
    * Version: v16.50.12.1453-v0.1,
    * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
    * Changelog:
      * v0.1:
        * Fix the board power cycling instead of rebooting issue
  * `descriptor.bin` - Intel Flash Descriptor
    * Version: v1.1,
    * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
    * Changelog:
      * v1.1:
        * Fix the board power cycling instead of rebooting issue
* `vp2430/`
  * `me.bin` - Intel Management Engine
    * Version: v16.50.15.1515,
    * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
    * Changelog:
      * v16.50.12.1453-v0.1:
        * Fix the board power cycling instead of rebooting issue
  * `descriptor.bin` - Intel Flash Descriptor
    * Version: v1.2,
    * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
    * Changelog:
      * v1.2:
        * Updated to the newest ME 16.50.15.1515
      * v1.1:
        * Fix the board power cycling instead of rebooting issue
  * `AlderLakeFspBinPkg/` - Intel Alder Lake-N Firmware Support Package
    * Version: 0C.02.89.30-v0.1
    * License: [Intel FSP/SIC Software License Agreement][INTEL FSP SIC SLA]
      with permission to use only on Protectli VP2430 platform
    * Changelog:
      * v0.1:
        * Always program CPU features on S3 resume
        * Add support for PchPciePowerGating and PchPcieClockGating
      * 0C.02.89.30 - base unmodified Intel FSP version
* `vp2430/`
  * `me.bin` - Intel Management Engine
    * Version: v16.50.15.1515,
    * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * `descriptor.bin` - Intel Flash Descriptor
    * Version: v1.0,
    * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]

Intel Management Engine and Flash Descriptor have been generated from Intel
CSME for Alder Lake-N 16.50.12.1453v2 and 16.50.15.1515v3.1 Consumer software
kit using genuine components provided by Intel, subject to the [PV Intel OBL
Software License Agreement 11.2.2017][INTEL SLA].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on [3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack).
Current signing key: [Dasharo release 0.9.x for Protectli signing key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[INTEL FSP SIC SLA]: ../../licenses/INTEL_FSP_SIC_LICENSE.txt
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/customer-keys/protectli/release-keys/dasharo-release-0.9.x-for-protectli-signing-key.asc
