
# SDL3 Template

Template for an SDL3 project that can be compiled for windows and linux

## Build
Linux
```
cmake .
cmake --build .
```
Windows
```
cmake -DCMAKE_TOOLCHAIN_FILE=./toolchain-mingw.cmake .
cmake --build .
```