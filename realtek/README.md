# Realtek blobs

The directory contains additional Realtek drivers needed to produce a full
Dasharo firmware image compatible with MSI PRO B850-P WIFI (and possible other
platforms).

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `RtkUndiDxe.efi` - UEFI x64 UNDI driver for Realtek PCIe Ethernet
  * Version: v2.080
  * License: [Realtek License][INTEL REALTEK_LIC]
* `edk2-lan-rom.json` - SBOM input file to add the `RtkUndiDxe.efi`
  information to coreboot's SBOM

The driver is available for download at [Realtek driver page][REALTEK_DRV].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on [3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack).
Current signing key:
[Dasharo release 0.x compatible with MSI MS-7E56 signing key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[REALTEK_LIC]: ../../licenses/RealtekLicense.txt
[REALTEK_DRV]: https://www.realtek.com/Download/ToDownload?type=direct&downloadid=3413
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/dasharo/msi_ms7e56/dasharo-release-0.x-compatible-with-msi-pro-b850-p-wifi-signing-key.asc
