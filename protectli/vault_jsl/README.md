# Protectli V1210/V1410/V1610 blobs

The directory contains blobs to produce a full Dasharo firmware image
for Protectli V1210/V1410/V1610 platforms.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `me.bin` - Intel Management Engine
  * Version: v13.50.27.1987,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.0,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `JasperLakeFspBinPkg` - Intel Firmware Support Package for JasperLake from
  JSL_BIOS_3332_00 software kit provided by Intel
  * Version: 2021/08/23 v2115,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]

Intel Management Engine and Flash Descriptor have been generated from Intel
CSE 13.50.27.1987v5 software kit using genuine components provided by Intel,
subject to the [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on
[3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack). Current signing key:
[Dasharo open-source firmware engineering release signing key][KEY] (an
engineering key is used, because platforms are not in production quality yet).

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/dasharo/dasharo-open-source-firmware-engineering-release-signing-key.asc
