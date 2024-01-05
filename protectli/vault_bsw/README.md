# Protectli FW4C blobs

The directory contains blobs to produce a full Dasharo firmware image
for Protectli FW4C platform.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `BraswellFspBinPkg` - Intel Firmware Support Package for Braswell platform,
  based on the public Braswell FSP 1.1.8.0
  * Version: v1.1.8.0.1,
  * License: [Intel FSP/SIC Software License Agreement][INTEL FSP SIC SLA]
    with permission to use only on Protectli FW4C platform
  * Changelog:
    * v1.1.8.0.1
      * Patch I2C PMIC configuration to match PMIC used on FW4C platform
    * v1.1.8.0.0 - unmodified public Braswell FSP 1.1.8.0

[INTEL FSP SIC SLA]: ../../licenses/INTEL_FSP_SIC_LICENSE.txt
