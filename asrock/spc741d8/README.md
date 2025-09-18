# ASRock Rack SPC741D8-2L2T/BCM blobs

The directory contains blobs to produce a full Dasharo firmware image
compatible with ASRock Rack SPC741D8-2L2T/BCM.

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is presented below.

* `me.bin` - Intel Server Platform Services
  * Version: v6.1.4.89.0,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
* `descriptor.bin` - Intel Flash Descriptor
  * Version: v1.0,
  * License: [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA]
  * Changelog:

Intel Management Engine and Flash Descriptor have been generated from Intel
SPS for Emmitsburg 6.1.4.89.0 software kit using genuine components provided by
Intel, subject to the [PV Intel OBL Software License Agreement 11.2.2017][INTEL SLA].

[INTEL SLA]: ../../licenses/pv%20intel%20obl%20software%20license%20agreement%2011.2.2017.pdf

You can verify the binary hashes using signatures made by the Dasharo release
keys for given platform available on 3mdeb-secpack. Current signing key:
Dasharo release 0.9.x compatible with ASRock Rack SPC741D8-2L2T signing key

gpg -v --verify SHA256SUMS.sig SHA256SUMS
sha256sum -c SHA256SUMS