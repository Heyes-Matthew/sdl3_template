Windows:
cmake -DCMAKE_TOOLCHAIN_FILE=./toolchain-mingw.cmake .
cmake --build .

Linux:
cmake .
cmake --build .