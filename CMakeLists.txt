#https://stackoverflow.com/questions/21163188/most-simple-but-complete-cmake-example
#https://crascit.com/2016/01/31/enhanced-source-file-handling-with-target_sources/

cmake_minimum_required(VERSION 3.0)

project(simpleSerialTest)

file(GLOB_RECURSE sources      src/*.cpp src/*.h)
add_library(SimpleSerial "")
add_subdirectory(src/simpleSerial)

# Set the output folder where your program will be created
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR})

add_executable(simpleSerialTest ${sources})
#target_link_libraries(simpleSerialTest src)


# just for example add some compiler flags
target_compile_options(simpleSerialTest PUBLIC -std=c++1y -Wall -Wfloat-conversion)

TARGET_LINK_LIBRARIES(simpleSerialTest PUBLIC -lpthread)

# this lets me include files relative to the root src dir with a <> pair
#target_include_directories(simpleSerialComms PUBLIC src/main)
