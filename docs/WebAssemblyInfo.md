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

## Running the Compiled Module

## Helpful Articles on WebAssembly