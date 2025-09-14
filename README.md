# Example CPP WebGL

This is a basic C++ cmake project example that uses emscripten to create a WebGL application.  The intent is to provide a working example with minimal dependencies.

Currently this project has only been built/tested on MacOS using xcode, which provides the compiler and OpenGL framework dependencies.  Emscripten is added as a submodule dependency, deps/emsdk/.

* Git clone this repo and update the submodules.

```
git clone https://github.com/shizgnit/example-cpp-webgl.git
cd example-cpp-webgl/
git submodule update --init --recursive
```

* Setup emscripten.  

Sourced from: https://emscripten.org/docs/getting_started/downloads.html

```
cd deps/emsdk/
./emsdk install latest
./emsdk activate latest
source ./emsdk_env.sh
```

* Building the code.

```
cd ../..
emcmake cmake -DCMAKE_TOOLCHAIN_FILE=`pwd`/deps/emsdk/upstream/emscripten/cmake/Modules/Platform/Emscripten.cmake .
cmake --build .
```
