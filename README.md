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

#### Windows w/ VSCode:

In order to use VSCode you need to install a compiler, such as GCC, Clang, or MSVC. You'll be prompted to select a kit to use, select the compiler of choice from the dropdown list. 

