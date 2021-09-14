cmake_minimum_required(VERSION 3.16)

project(GDNATIVE_CPP_EXAMPLE
LANGUAGES CXX)

include(FetchContent)

# The repo of godot-cpp
FetchContent_Declare(
	godot-cpp
	GIT_REPOSITORY https://github.com/errata-c/godot-cpp.git
	GIT_TAG master
)
# Includes godot-cpp package, builds a target godot::cpp
FetchContent_MakeAvailable(godot-cpp)

# Add the gdnative library, MUST be a SHARED library, except on iOS, as it only allows static linking (Note that iOS support is UNTESTED for godot-cpp)
add_library(gdnative_cpp SHARED
	"src/gdexample.cpp"
	"src/gdlibrary.cpp"
	"src/gdexample.h"
)
# Link to the library
target_link_libraries(gdnative_cpp PRIVATE godot::cpp)

# Automatically install the library into the actual godot project
# Note that this function is part of the godot-cpp cmake package
install_gdnlib(
	# The name of the target library to install
	TARGET gdnative_cpp
	
	# The destination to install it to.
	# Assumed to be a directory inside a pre-existing godot project directory.
	# Note that if you specify a relative destination, it will assume its relative to CMAKE_INSTALL_PREFIX
	DESTINATION "${CMAKE_CURRENT_SOURCE_DIR}/demo/bin" 
	
	# List of classes added by your gdnative library, you are allowed to specify as many as you need.
	# NOTE: This must be the actual name of the class in c++! The file generated for each will have a snake_case name to follow convention.
	CLASSES "GDExample" 
	
	# Other unused but potentially useful arguments supported by this function:
	
	# EXCLUDE_FROM_ALL -> Exclude this installation from the default install
	# NAME <string> -> Specify a name for your GDNative library other than the name of the target
	# SYMBOL_PREFIX <string> -> Override the default symbol prefix, see https://docs.godotengine.org/en/stable/classes/class_gdnativelibrary.html#class-gdnativelibrary-property-symbol-prefix (default: godot_)
	# COMPONENT <name> -> specify a component that this install command will be a part of
	# SINGLETON <TRUE/FALSE> -> Require that the library be loaded as a singleton if set to true (default: FALSE)
	# LOAD_ONCE <TRUE/FALSE> -> The library is not allowed to be loaded multiple times simultaneously when false, this may break things if set to true! (default: TRUE)
	# RELOADABLE <TRUE/FALSE> -> The library can be reloaded if true (default: TRUE)
	
	# DEPENDENCIES <target or file>... -> Specify a list of target or library dependencies to be installed as well
	# CONFIGURATIONS <config>... -> Specify a whitelist of configurations this install rule is for
	# PERMISSIONS <permissions>... -> Specify a list of file permissions for the installed files, see https://cmake.org/cmake/help/latest/command/install.html#files
)