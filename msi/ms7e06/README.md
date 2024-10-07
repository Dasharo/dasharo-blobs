# MSI MS-7E06 blobs

The directory contains blobs to produce a full Dasharo firmware image
compatible with MSI PRO Z790-P variants (DDR4 and DDR5 with or without WIFI).

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `me.bin` - Intel Management Engine
  * Version: v16.1.30.2307,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.2,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Changelog:
    * v1.2
      * Shrinked DevExp2 region and enlarged BIOS region to 28MiB
    * v1.1
      * Enable ME and Flash Descriptor region read-write access
    * v1.0 - initial version
* `microcode.bin` - Intel microcode update file
  * Version:
    * 0x36 for CPUIDs 00090672, 00090675, 000b06f2, 000b06f5
    * 0x12B for CPUID 000b0671
  * License [Intel production microcode license][INTEL_UCODE]

Intel Management Engine and Flash Descriptor have been generated from Intel
CSME for Raptor Lake-S 16.1.30.2307v4 Consumer software kit using genuine
components provided by Intel, subject to the
[PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].
Apart from the components in the CSME software kit, a Chipset Initialization
binary has been generated from the Intel PCH Chipset Initialization Kit
v160.02.99.1014, subject to the
[PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on [3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack).
Current signing key:
[Dasharo release 0.x compatible with MSI MS-7E06 signing key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[INTEL UCODE]: ../../licenses/LICENSE_UCODE_PROD.md
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/dasharo/msi_ms7e06/dasharo-release-0.x-compatible-with-msi-ms-7e06-signing-key.asc
