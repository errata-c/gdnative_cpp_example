GDNative C++ Example
====================

This repository contains the example GDNative C++ library in support of this tutorial:
http://docs.godotengine.org/en/latest/tutorials/plugins/gdnative/gdnative-cpp-example.html

It is now based on the new NativeScript 1.1 Godot-cpp bindings library and will only work with Godot 3.1 and onwards.
Switch to the `3.0` branch to see the original NativeScript 1.0 version.

## Dependencies:

#### Python 3

#### Git

## Build instructions:

#### Windows w/ visual studio 2019:

​	Open the repo folder in MSVC, wait for it to configure the project (if it doesn't configure it automatically, just click 'Project->configure project'). Optionally click on the configuration at the top (it should say 'x64-Debug' by default) and then click 'Manage Configurations...' to add a different configuration such as 'x64-Release'. Then click 'Build->Build All' to build the project. It will have to build some 600+ files so be patient. Finally click 'Build->Install GDNATIVE_CPP_EXAMPLE' to install the binaries into the demo project. You can then just open the project (in the 'demo' folder) in Godot to test it.

#### Windows or Linux w/ VSCode:

​	In order to use VSCode you need to install a compiler, such as GCC, Clang, or MSVC. You will also want to install the CMake addon to ease the process. Once the CMake addon is installed you'll be prompted to select a kit to use, just select the compiler of choice from the dropdown list. After the project configures, click the build button at the bottom of  window or use the hotkey Ctrl+Shift+P to open the command menu to select the CMake:Build command. Then after a successful build use the same hotkey to open command menu and select CMake:Install.

#### Windows or Linux command line:

​	CD to the repo directory, and configure the project with `cmake -S ./ -B ./build -D CMAKE_BUILD_TYPE=Debug` (you can change the build type to any of the supported types). Then build with `cmake --build ./build`, and install with `cmake --install ./build`.

## Running the Godot project

​	Once the library is built and installed, you just need to find the demo directory and import it in the Godot project manager. Then you can open the project and run the main scene to see a Godot icon in the top left corner of the window moving around, as well as messages reporting the positioning of the icon in the console.
