# Preparing redistributable blobs

To ensure that users and developers can build fully functional firmware images
for our platforms, we must provide not only the source code, but also the
necessary binary blobs required for coreboot to operate correctly.

These blobs are typically proprietary and subject to strict licensing terms. 
In most cases, we have successfully obtained redistribution rights, allowing 
us to legally share them. However, due to licensing restrictions, these blobs 
cannot be stored directly within the coreboot repository.

Instead, we maintain them in a dedicated repository — 
[dasharo-blobs](https://github.com/dasharo/dasharo-blobs) — where each binary 
is accompanied by relevant licensing information and integrity checksums. This 
repository adheres to clearly defined sourcing and preparation guidelines, 
ensuring full compliance with licensing requirements and transparency for end 
users.

The process can be split into

* Obtaining a stock binary
* Syncing with Intel for the most recent tool packages (`CSME`, `FSP`,
  `GraphicsPkg`)
* Extracting the binary to obtain the base layout and configuration using
  `MFIT`
  * Replacing the vendor-provided binaries with clean ones from the CSME package
  * Building the IFD and ME binaries
* Uploading to dasharo-blobs

## Obtaining a stock binary

A dump of the vendor's original proprietary firmware should be available from
our initial HCL dump of the platform, done upon receiving it. Look for your
platform's name in the [HCL report folder](link) on our cloud, and pick the
package without `*Dasharo*` in its name. If you unpack it, the firmware ROM
should be available as `logs/rom.bin`.

If for some reason that route is not viable, you should look for a publicly
available firmware update file for the platform online.

## Syncing with Intel for the most recent tool packages

* FSP
* GraphicsPkg
* CSME

... **TODO** @mkopec

## Decomposing with the MFIT tool

![](../img/mfit-home.png)

MFIT usually comes in two versions - Linux and Windows, and they can be found
in the CSME package under the following paths:

* `Tools/System_Tools/MFIT/Linux64/mfit`
* `Tools/System_Tools/MFIT/Windows/mfit.exe`

You might want to try whether the Linux version or the Windows version ran
through wine works better on your system.

To decompose a stock firmware image, run MFIT and click on the `Decompose an
image` icon, then choose your image. If you run into an error about MFIT not
being able to create files in the chosen directory, change the folder's default
privilege settings.

Having the image decomposed, you can take a peek inside and start replacing the
vendor-customized binaries with stock clean ones directly from Intel.

## Replacing the binaries 

Looking at the Meteor Lake CSME as an example, the clean replacement blobs are
located in the `Image Components` folder, which is structured as follows:

```
Image Components
├── 3rd party Licenses in Security FW
│   ├── (...) not interesting
├── CSME
│   └── Silicon
│       └── M
│           ├── CSME_Corporate_18.0.10.2351_prod.bin
│           └── CSME_TRACE_EXT_18.0.10.2351.traceext
├── DMU
│   └── DMU_8102.207a.0.4200_prod.bin
├── Intel(R) Silicon Security Engine
│   └── SSE_1000.0.5.2056_prod.bin
├── PMC
│   ├── PMC_1800.15.00.1060_preprod.bin
│   ├── PMC_1800.15.00.1060_prod.bin
│   └── PMC_TRACE_EXT_1800.15.00.1060.xml
├── PRESTITCHED
│   └── FWUpdate_prod_Corporate..bin
├── PUNIT
│   └── PUNIT_102.807a.0.4200_prod.bin
├── SOCC
│   ├── SOCC_MTL_P_ALL_1800.15.0.1037_Release_ALL_Prod_PV0.bin
│   └── SOCC_MTL_P_ALL_1800.15.0.1037_Release_ALL_Prod_PV1.bin
├── SPHY
│   └── SPHY_18.1.1.7053_prod.bin
└── TCSS
    ├── IOM
    │   └── IOM_30.001a.0.0_prod.bin
    ├── NPHY
    │   └── NPHY_18.1.0.7013_prod.bin
    ├── Retimer
    │   ├── HBR_MTLARL_ALL_ALL_6.24.2V2_Rel_ALL_SEC1_PROD_external_sign.bin
    │   └── HBR_MTLARL_ALL_ALL_6.24.2V2_Rel_ALL_SEC1_PROD_MTL_LP5xT4_TCP0_1_sign.bin
    └── TBT
        └── TBT_MTLARL_HU_ALL_13.1V3_Rel_ALL_Prod_PV1_SEC0_signed.bin
 ```

Having decomposed the vendor firmware image, you now have to replace each
vendor-configured binary with the clean ones from this directory.

![](../img/mfit-open.png)

You can go on a scavenger hunt and look through every field in the MFIT tool in
search for their respective slots, familiarizing yourself with the firmware
binary structure, or you can help yourself to the cheatsheet below - matching
MFIT menu path on the left to binary name on the right.

```
* Flash Layout / Me and Pmc Region / ME Binary File : CSME_Corporate_18.0.10.2351_prod.bin
* Flash Layout / Me and Pmc Region / PMC Binary File : PMC_1800.15.00.1060_prod.bin
* Flash Layout / Sub partitions / SOC Configuration File : SOCC_MTL_P_ALL_1800.15.0.1037_Release_ALL_Prod_PV1.bin
* Flash Layout / Sub partitions / Intel Silicon Security Engine Package / Intel Silicon Security Engine Sub Partition / SSE Section Binary : SSE_1000.0.5.2056_prod.bin
* Flash Layout / Sub partitions / Intel Silicon Security Engine Package / Intel Silicon Security Engine Sub Partition / DMU Sub Partition / DMU Section Binary : DMU_8102.207a.0.4200_prod.bin
* Flash Layout / Sub partitions / Intel Silicon Security Engine Package / Intel Silicon Security Engine Sub Partition / PUNIT Sub Partition / PUNIT Section Binary : PUNIT_102.807a.0.4200_prod.bin
* Flex IO / SPHY Configuration / PHY Binary Configuration File : SPHY_18.1.1.7053_prod.bin
* Flex IO / TCSS Configuration / IO Manageability Engine Binary File : IOM_30.001a.0.0_prod.bin
* Flex IO / TCSS Configuration / NPHY Binary File : NPHY_18.1.0.7013_prod.bin
* Flex IO / TCSS Configuration / Thunderbolt Binary File : TBT_MTLARL_HU_ALL_13.1V3_Rel_ALL_Prod_PV1_SEC0_signed.bin
```

After successfully replacing the binaries, it's time to build the image. If you
see the error:

```
ERROR    : Failed to build container: CsePlugin:CSE_SOCC
ERROR    : The PV bit in PCHC is off while CSE image is of PV/post PV release. Please re-sign the partition with PV bit on..
Source: 'CsePlugin:CSE_SOCC'
```

You probably chose the `SOCC_MTL_(...)_Prod_PV0.bin` instead of
`SOCC_MTL_(...)_Prod_PV0.bin`.

## Uploading to dasharo-blobs

* Clone the [dasharo-blobs](https://github.com/dasharo/dasharo-blobs) repo
* Navigate to, or create, `manufacturer/model/` directory
* Place the blobs in the directory
* Generate the `SHA256SUMS` file as per dasharo-blobs README
* Create and fill out the `README.md` _in your directory_ with license
  information - see how it's done for other platforms and follow suit. Here's
  a fragment of the V5X0TU README:

  ```
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
  ```
  
  For the exact licensing details, best consult your TL/PM.
* Commit, push, open a PR and ask the keyholder to sign your SHA256SUMS file -
  that will likely be your TL.
