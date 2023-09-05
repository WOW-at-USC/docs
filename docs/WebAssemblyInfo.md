---
layout: default
title: WebAssembly Info
nav_order: 2
---


# WebAssembly Info

This page will outline basic WebAssembly usage steps, including setting up the Emscripten compiler and running a basic WebAssembly module.

## Emscripten
[Emscripten](https://emscripten.org/index.html) is a C/C++-to-WebAssembly compiler that we use frequently in our projects. As such, it's likely that you will need to install and use it. 

### Installation
The full installation instructions can be found on the [project's page](https://emscripten.org/docs/getting_started/downloads.html), but the quick commands are:
```sh
#Taken from https://emscripten.org/docs/getting_started/downloads.html

git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk install latest
./emsdk activate latest
source ./emsdk_env.sh
```

### Compiling and Running a WebAssembly Module (from C/C++)
After running the `source` command in the installation, `emcc` should be a valid command in your terminal shell. Suppose we have a simple C file named `simple.c`:
```c
// simple.c
#include <stdio.h>

int main(){
    printf("Hello, world!");
    return 0;
}
```

To compile this file with Emscripten, we would run 
```
emcc simple.c -o simple.wasm
```
to generate a wasm file named `simple.wasm`. You can also run other compilation options, such as specifying optimization levels, by adding the appropriate flag to the command. For example, to compile with an aggresive optimization level, you can run
```
emcc -O3 simple.c -o simple.wasm
```
A detailed list of other compilation options for the `emcc` command can be found on [this Emscripten page](https://emscripten.org/docs/tools_reference/emcc.html).

Additionally, Emscripten can generate JavaScript and HTML glue code necessary to run  the module in an emulated terminal directly in the browser. To do this, we would use this command instead of the previous one:
```
emcc simple.c -o simple.html
```
This will generate the necessary .wasm, .js, and .html files to run the module in a browser. 

 To run this sample, you will need a webserver to host the directory containing the generated web files. Using Node.js (which is installed with Emscripten), you can start a simple webserver by running the following command within the desired directory:
 ```sh
 npx serve
 ```
 A localhost address should be printed out that you can use to view the .html file.

 In the browser, any errors in WebAssembly will be logged to the Inspector Console, which can be accessed on Chrome or Firefox by right-clicking on the page and clicking "Inspect". The Console tab will contain the logged output of the webpage, including any WebAssembly-related logs.


## WABT 
[WABT](https://github.com/WebAssembly/wabt) is a toolset that contains utilities you will most likely need in your projects, particularly the `wasm2wat` and `wat2wasm` conversion tools. To install Wabt on Debian-based Linux distros, you can simply run
```
sudo apt install wabt
```
To install on Windows or Mac, you can find download the appropriate [pre-built release](https://github.com/WebAssembly/wabt/releases) and uncompress the archive. The tools can be run in the `bin` directory through the CLI. To make this easier, I would move the unarchived wabt folder to a stable folder path and add the `bin` folder to the system PATH.

The most useful tools will be `wasm2wat` and `wat2wasm`. To covert a .wasm file to a .wat file, you can run the following in the `bin` directory
```
wasm2wat <path/to/wasm>.wasm -o <path/to/output/to>.wat
```

Similarly, to convert a .wat file .wasm, you can run the following 
```
wat2wasm <path/to/wat>.wat -o <path/to/output/to>.wasm
```

The WABT documentation contains [more examples](https://github.com/WebAssembly/wabt#running-wat2wasm) on these two commands.

## Viewing WebAssembly files
In order to view the WebAssembly files, you can use any text editor to view files in the WebAssembly text format (.wat). I would recommend using the [Visual Studio Code](https://code.visualstudio.com/) editor as it has a [WebAssembly extension](https://marketplace.visualstudio.com/items?itemName=dtsvet.vscode-wasm) that makes it simple to view .wasm files as .wat files automatically. In addtion, it supports syntax highlighting with WebAssembly modules. Through the right-click menu, it can also convert between .wasm and .wat files in the editor.


## Helpful Articles on WebAssembly
- WebAssembly Core Specification: [https://webassembly.github.io/spec/core/index.html#](https://webassembly.github.io/spec/core/index.html#)
- High-Level overview from Mozilla: [https://developer.mozilla.org/en-US/docs/WebAssembly/Concepts](https://developer.mozilla.org/en-US/docs/WebAssembly/Concepts)
- Compilation Guide from Mozilla: [https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm](https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm)
- WebAssembly Compilation Pipeline in V8 (Chromium Engine): [https://v8.dev/docs/wasm-compilation-pipeline](https://v8.dev/docs/wasm-compilation-pipeline) 