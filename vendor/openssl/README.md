# OpenSSL Static Libraries

This directory contains pre-compiled static libraries of OpenSSL for various architectures.

**Version**: 3.3.1
**License**: Apache License 2.0
**Source**: [https://www.openssl.org/](https://www.openssl.org/) or [https://github.com/openssl/openssl](https://github.com/openssl/openssl)

## Directory Structure

*   `linux-x86_64`: Static libraries and headers for Linux x86_64 (built with `manylinux_2_28_x86_64`)
*   `linux-aarch64`: Static libraries and headers for Linux AArch64 (built with `manylinux_2_28_aarch64`)

## How to update

These libraries are built using the GitHub Actions workflow in `.github/workflows/build-openssl.yml`.
To update:
1. Trigger the "Build OpenSSL Static Linux" workflow.
2. Download the artifacts from the GitHub Release.
3. Replace the content in the respective directories.

## Usage in build scripts

When linking against these libraries, ensure you include `-ldl` and `-lpthread` as they are required by OpenSSL.

Example (pkg-config):
```bash
export OPENSSL_DIR=$(pwd)/vendor/openssl/linux-x86_64
export PKG_CONFIG_PATH=$OPENSSL_DIR/lib/pkgconfig:$PKG_CONFIG_PATH
# Configure build...
```
