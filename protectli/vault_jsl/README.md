# Protectli V1210/V1410/V1610 blobs

The directory contains blobs to produce a full Dasharo firmware image
for Protectli V1210/V1410/V1610 platforms.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `{V1210,V1410,V1610}/me.bin` - Intel Management Engine
  * Version: v13.50.27.1987,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `V1410/descriptor.bin` - Intel Flash Descriptor
  * Version: v1.1,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Changelog:
    * V1.1:
      * Enable SATA1 on Multi Flex Combo port 0 (SATA1/PCIE8/USB6) to support
        M.2 SATA disk in NVMe slot
      * Enable PCIe on Multi Flex Combo port 1 (SATA0/PCIE7) to support
        NVMe disk with x1 link in NVMe slot
* `V1610/descriptor.bin` - Intel Flash Descriptor
  * Version: v1.1,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Changelog:
    * V1.1:
      * Change SPA bifurcation to 2x2 to get NVMe link x2
      * Enable PCIe on Multi Flex Combo port 0 and 1 to support NVMe with x2
        link in NVMe slot slot (the strap is patched to SATA dynamically based
        on detected disk in coreboot)
* `V1210/descriptor.bin` - Intel Flash Descriptor
  * Version: v1.1,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Changelog:
    * V1.2:
      * Change SPA bifurcation to 1x2, 2x1 to get NVMe link x2
      * Enable SATA0 on Multi Flex Combo port 0 (SATA0/PCIE7/USB5) to support
        M.2 SATA disk in NVMe slot
    * V1.1:
      * Change SPA bifurcation to 2x2 to get NVMe link x2
      * Enable SATA1 on Multi Flex Combo port 0 (SATA1/PCIE8/USB6) to support
        M.2 SATA disk in NVMe slot
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
[Dasharo release 0.9.x for Protectli signing key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/customer-keys/protectli/release-keys/dasharo-release-0.9.x-for-protectli-signing-key.asc
