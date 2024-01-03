# Protectli VP2410 blobs

The directory contains blobs to produce a full Dasharo firmware image
for Protectli VP2410 platform.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `ifwi.bin` - Intel Management Engine/Trusted Execution Engine
  * Version: v4.0.50.2083,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.0,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `GeminiLakeFspBinPkg` - Intel Firmware Support Package for GeminiLake, based
  on the GeminiLake Silicon Initialization Code 2.2.1.3 obtained from Intel
  * Version: v2.2.1.3.2,
  * License: [Intel FSP/SIC Software License Agreement][INTEL FSP SIC SLA]
    with permission to use only on Protectli VP2410 platform
  * Changelog:
    * v2.2.1.3.2
      * Improved memory information reporting
    * v2.2.1.3.1
      * Fixed the scripts and code to build FSP with EDK2 vUDK2017 and GCC
      * Added proper debug libraries to all modules allowing complete
        debugging of the FSP during boot
      * Fixed handling MRC cache when CSE boot assistance is not leveraged
      * Updated Graphics PEIM to a newer version
      * Program CLKREQ GPIO RX/TX bits only when PCIe power sequencing is not
        skipped
      * Disable DPTF BAR programming by FSP, breaking the PCI enumeration in
        coreboot and conflicting PCI resources with graphics
      * Fixed VT-d initialization as per Geminilake IAFW Specification
      * Skip setting IA untrusted mode in FSP, coreboot already does it
      * Allow configuring USB SSIC ports with FSP UPDs
    * v2.2.1.3.0 - unmodified GeminiLake Silicon Initialization Code 2.2.1.3

Intel Management Engine/Trusted Execution Engine and Flash Descriptor have
been generated from Intel TXE 4.0.50.2083 software kit using genuine
components provided by Intel, subject to the
[PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on [3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack).
Current signing key: [Dasharo release 1.1.x for Protectli signing key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[INTEL FSP SIC SLA]: ../../licenses/INTEL_FSP_SIC_LICENSE.txt
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/customer-keys/protectli/release-keys/dasharo-release-1.1.x-for-protectli-signing-key.asc
