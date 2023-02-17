# Interactive TPM simulator with codelabs

## Overview

TPM2-JS lets you experiment with a software
[TPM](https://en.wikipedia.org/wiki/Trusted_Platform_Module) device in your
browser. It's an educational tool that teaches you how to use a TPM device to
secure your workflows. The codelab like sessions cover topics such as key
generation, measured boot, remote attestation and sealing.

## Screenshots

Welcome screen: ![Welcome Screen](docs/screenshot_welcome.png)

Keys codelab: ![Keys codelab](docs/screenshot_keys.png)

PCRs codelab: ![PCRs codelab](docs/screenshot_pcrs.png)

## Dependencies for Windows
*   Docker
*   Python3

## Architecture

TPM2-JS includes the following libraries:

*   Intel [TPM2 TSS](https://github.com/tpm2-software/tpm2-tss).
*   IBM [software TPM simulator](https://sourceforge.net/projects/ibmswtpm2/).
*   Google [BoringSSL](https://boringssl.googlesource.com/boringssl).

The libraries are compiled to
[WebAssembly](https://en.wikipedia.org/wiki/WebAssembly), and accessed via
Javascript.

You can build the project using the provided Docker file.

One time initialization:

```shell
./dcmake.sh
```

Then build using:

```shell
./dmake.sh -j4
```

## Serve Files

Check and add the line `application/wasm wasm` to `/etc/mime.types` if it doesn't exist already.

Serve files from the built web package:

```shell
cd build-web/web
python3 -m http.server --bind 127.0.0.1 8000
```
