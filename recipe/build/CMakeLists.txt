cmake_minimum_required(VERSION 3.8)
project(MediaInfo_CLI VERSION 25.04 LANGUAGES CXX)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../../../Source)

# Source files
file(GLOB CLI_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/../../../Source/CLI/*.cpp)

# Find required packages
find_package(ZLIB REQUIRED)
find_package(Threads REQUIRED)

# Main executable
add_executable(mediainfo ${CLI_SOURCES})

# Link libraries
target_link_libraries(mediainfo
    PRIVATE
    MediaInfoLib
    ZenLib
    ZLIB::ZLIB
    Threads::Threads
)

# Installation
install(TARGETS mediainfo DESTINATION bin)
