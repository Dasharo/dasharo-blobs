# Novacustom NV4XMB/ME/MZ blobs

The directory contains blobs to produce a full Dasharo firmware image
for Novacustom NV4XMB/ME/MZ laptops.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `me.bin` - Intel Management Engine
  - Version: v15.0.47.2473,
  - License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `descriptor.bin` - Intel Flash Descriptor
  - Version: v1.0,
  - License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `IntelGopDriver.efi` - Intel GOP Driver
  - Version: v17.0.1087,
  - License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]

Intel Management Engine and Flash Descriptor have been generated from Intel
CSME for Tiger Lake-U 15.0.47.2473v3 Consumer software kit using genuine
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

## Other files

* `vbt.sjf` - Configuration parameters for Intel Video BIOS Table blob
  - Configuration data for generating Intel Video BIOS Table. Extracted from
    vendor firmware, may be used with Intel DisCon utility and VBT samples from
    [Intel FSP repository](https://github.com/intel/FSP/tree/master/TigerLakeFspBinPkg/Client/SampleCode/Vbt)
    to generate a new VBT.
