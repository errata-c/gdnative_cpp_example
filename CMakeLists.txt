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

# Add the gdnative library, MUST be a SHARED library (except on iPhone? I dislike apple)
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
	TARGET chess-training 
	
	# The destination to install it to.
	# Assumed to be a directory inside a pre-existing godot project directory.
	# Note that if you specify a relative destination, it will assume its relative to CMAKE_INSTALL_PREFIX
	DESTINATION "${CMAKE_CURRENT_SOURCE_DIR}/demo/bin" 
	
	# List of classes added by your gdnative library
	CLASSES "GDExample" 
)