# ttutil library

This is an unofficial repository of TTUTIL Fortran library used by the SWAP code. I made a build system for it to enable automated build and release of the SWAP code for Windows and Linux machines.

Pixi is used for package management and mason is the build system.

## How does this work?

### On local machine

During development, to get new executable, run pixi task:

- build-linux - to build the linux executable
- build-windows-cross - to build the windows executable on a linux machine
- build-windows-native - to build the windows executable on a windows machine

## Obtaining the latest release

you can make a post request or use curl/wget to download this into your repository.

https://github.com/SWAP-model/ttutil/releases/latest/download/libttutil427_windows.a
https://github.com/SWAP-model/ttutil/releases/latest/download/libttutil427_linux.a