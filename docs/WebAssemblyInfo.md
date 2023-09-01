---
layout: default
title: WebAssembly Info
nav_order: 2
---


# WebAssembly Info

This page will outline basic WebAssembly usage steps, including setting up the Emscripten compiler and running a basic WebAssembly module.

## Setting Up Emscripten
Emscripten is a C/C++-to-WebAssembly compiler that we use frequently in our projects. As such, it's likely that you will need to install and use it. The full installation instructions can be found on the [project's page](https://emscripten.org/docs/getting_started/downloads.html), but the quick commands are:

```sh
#Taken from https://emscripten.org/docs/getting_started/downloads.html

git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk install latest
./emsdk activate latest
source ./emsdk_env.sh
```

## Compiling and Running a WebAssembly Module (from C/C++)




## Helpful Articles on WebAssembly
- WebAssembly Core Specification: [https://webassembly.github.io/spec/core/index.html#](https://webassembly.github.io/spec/core/index.html#)
- High-Level overview from Mozilla: [https://developer.mozilla.org/en-US/docs/WebAssembly/Concepts](https://developer.mozilla.org/en-US/docs/WebAssembly/Concepts)
- Compilation Guide from Mozilla: [https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm](https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm)
- WebAssembly Compilation Pipeline in V8 (Chromium Engine): [https://v8.dev/docs/wasm-compilation-pipeline](https://v8.dev/docs/wasm-compilation-pipeline) 