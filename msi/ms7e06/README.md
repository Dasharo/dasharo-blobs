# MSI MS-7E06 blobs

The directory contains blobs to produce a full Dasharo firmware image
compatible with MSI PRO Z790-P variants (DDR4 and DDR5 with or without WIFI).

* `me.bin` - Intel Management Engine 16.1.30.2255, subject to
  [INTEL SOFTWARE LICENSE AGREEMENT][INTEL SLA]
* `descriptor.bin` - Intel Flash descriptor, subject to
  [INTEL SOFTWARE LICENSE AGREEMENT][INTEL SLA]

Intel Management Engine and Flash descriptor have been generated from Intel
CSME for Raptor Lake-S 16.1.30.2255v5 Consumer software kit using genuine
components provided by Intel, subject to the [INTEL SOFTWARE LICENSE AGREEMENT][INTEL SLA].
Apart from the components in the CSME software kit, a Chipset Initialization
binary has been generated from the Intel PCH Chipset Initialization Kit
v160.02.99.1014, subject to the [INTEL SOFTWARE LICENSE AGREEMENT][INTEL SLA].

By using above components you agree to the
[INTEL SOFTWARE LICENSE AGREEMENT][INTEL SLA].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on [3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack).
Current signing key:
[Dasharo release 0.x compatible with MSI MS-7E06 signing key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[KEY]: https://github.com/3mdeb/3mdeb-secpack/blob/master/dasharo/msi_ms7e06/dasharo-release-0.x-compatible-with-msi-ms-7e06-signing-key.asc
