# dasharo-blobs
Repository containing extra assets for use with Dasharo

# Licenses

Do not use or load software from this repository until you have carefully read
the licenses assigned to the relevant components. By downloading or using the
software component from this repository, you agree to the terms of license
associated with the given software component. If you do not wish to so agree,
do not install or use the software from this repository. Association of the
software components and licenses is outlined in the respective READMEs in the
subdirectories.

# Creating SHASUMS

Example how to create SHA256SUMS for all file with `.bin` extension:

```bash
sha256sum `find . -name "*.bin"` > SHA256SUMS
```
