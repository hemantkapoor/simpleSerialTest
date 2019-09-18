#https://stackoverflow.com/questions/21163188/most-simple-but-complete-cmake-example
cmake_minimum_required(VERSION 3.0)

project(simpleSerialTest)

file(GLOB_RECURSE sources      src/*.cpp src/*.h src/comms/*.cpp src/comms/*.h src/utility/*.cpp src/utility/*.h)

# Set the output folder where your program will be created
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR})

add_executable(simpleSerialComms ${sources})

# just for example add some compiler flags
target_compile_options(simpleSerialComms PUBLIC -std=c++1y -Wall -Wfloat-conversion)

TARGET_LINK_LIBRARIES(simpleSerialComms PUBLIC -lpthread)

# this lets me include files relative to the root src dir with a <> pair
target_include_directories(simpleSerialComms PUBLIC src/main)


###############################################################################
## packaging ##################################################################
###############################################################################

# all install commands get the same destination. this allows us to use paths
# relative to the executable.
install(TARGETS simpleSerialComms DESTINATION simpleSerialComms_destination)

# now comes everything we need, to create a package
# there are a lot more variables you can set, and some
# you need to set for some package types, but we want to
# be minimal here
set(CPACK_PACKAGE_NAME "simpleSerialComms_destination")
set(CPACK_PACKAGE_VERSION "1.0.0")

# we don't want to split our program up into several things
set(CPACK_MONOLITHIC_INSTALL 1)

# This must be last
include(CPack)

