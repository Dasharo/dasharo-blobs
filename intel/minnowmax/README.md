# Intel MinnowBoard Turbot blobs

The directory contains blobs to produce a full Dasharo firmware image
compatible with Intel MinnowBoard Turbot platforms.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `txe.bin` - Intel Trusted Execution Engine
  * Version: v1.1.4.1145v3,
  * License: [Tianocore license][INTEL TIANOCORE]
  * Source: [tianocore-training repository][TXE]
* `txe_sb.bin` - Intel Trusted Execution Engine provisioned with TXE Secure
  Boot evaluation keys in fuse emulation mode
  * Version: v1.1.4.1145v3,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.0,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Based on the descriptor from [tianocore-training repository][DESCRIPTOR]
    but with TXE region shrinked to 2MB and GBE region removed.
* `IntelGopDriver.efi` - Graphics Output Protocol EFI driver
  * Version: 7.2.1011
  * License: [Tianocore license][INTEL TIANOCORE]
  * Source: [tianocore-training repository][GOP]
* `mrc.elf` - Intel Memory Reference Code
  * Version: v0.97
  * Source: [MrChromebox repository][MRC]
  * License: Not specified, redistributable

Intel Trusted Execution Engine, Flash Descriptor and GOP driver have been
sourced from [Tianocore Training
repository](https://github.com/tianocore-training/PlatformBuildLab_FW/)
subject to the [Tianocore license][INTEL TIANOCORE].

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on
[3mdeb-secpack](https://github.com/3mdeb/3mdeb-secpack). Current signing key:
[Dasharo release 0.9.x compatible with MinnowBoard Turbot signing key][KEY].

```bash
gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS
```

The directory also contains TXE Secure Boot keys used for **evaluation and
testing only**:

* `oem_key_priv_sample.pem` - Sample key used to sign Key Manifest and
  authorize Secure Boot Manifest key. Provisioned as Secure Boot key hash in
  TXE.
* `sb_key_priv_sample.pem` - Sample key used to sign Secure Boot Manifest.

They are used to build-test and validate TXE Secure Boot functionality on
MinnowBaord Turbot Bay Trail platform. The same keys have been provisioned in
`txe_sb.bin` using fuse emulation mode. As long as fuse emulation mode is
active, fusing the platform permanently is not possible.

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf
[INTEL TIANOCORE]: https://github.com/tianocore-training/PlatformBuildLab_FW/blob/master/LICENSE.txt
[KEY]: https://github.com/3mdeb/3mdeb-secpack/dasharo/minnowboard_turbot/dasharo-release-0.9.x-compatible-with-minnowboard-turbot-signing-key.asc
[TXE]: https://github.com/tianocore-training/PlatformBuildLab_FW/blob/master/FW/PlatformBuildLab/Max/silicon/Vlv2MiscBinariesPkg/SEC/1.1.4.1145v3/VLV_SEC_REGION.bin
[DESCRIPTOR]: https://github.com/tianocore-training/PlatformBuildLab_FW/blob/master/FW/PlatformBuildLab/Max/edk2-platforms/Vlv2TbltDevicePkg/Stitch/IFWIHeader/IFWI_HEADER.bin
[GOP]: https://github.com/tianocore-training/PlatformBuildLab_FW/blob/master/FW/PlatformBuildLab/Max/silicon/Vlv2MiscBinariesPkg/GOP/7.2.1011/RELEASE_VS2008x86/X64/IntelGopDriver.efi
[MRC]: https://github.com/MrChromebox/blobs/blob/917ea7bb2eb72c754056182f4e7f2b7e252396fd/soc/intel/byt/mrc.elf