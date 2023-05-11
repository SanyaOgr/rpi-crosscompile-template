# rpi-crosscompile-template
Basic C++ Linux project template with instruction how to cross-compile it for Raspberry PI

## Setup
* Install arm toolchain
```shell
sudo apt-get install g++-arm-linux-gnueabihf binutils-arm-linux-gnueabihf
```
* Check that it's works
```shell
arm-linux-gnueabihf-g++ -v 
arm-linux-gnueabihf-ld -v
```
* Create `rootfs` folder (`~/raspberrypi/rootfs` in example)
* Copy folders `/lib` and `/usr` from Raspberry system to this folder
* Change the `rootfs` path in `rpi-toolchain.cmake` to your path
```cmake
SET(CMAKE_FIND_ROOT_PATH "$ENV{HOME}/raspberrypi/rootfs")
```

## Build
```shell
mkdir build && cd build
cmake -DCMAKE_DUILD_TYPE=Release -DCMAKE_TOOLCHAIN_FILE=rpi-toolchain.cmake ..
cmake --build .
```
