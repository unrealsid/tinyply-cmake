cmake_minimum_required(VERSION 4.0.0)

# Compiler requirements
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

project(tinyply LANGUAGES CXX)
set(PROJECT_VERSION 2.3)

# Library
set(SHARED_LIB false CACHE BOOL "Build as shared library")
if(${SHARED_LIB})
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
    add_library(tinyply SHARED source/tinyply.cpp source/tinyply.h)
else()
    add_library(tinyply STATIC source/tinyply.cpp source/tinyply.h)
endif()

target_include_directories(
        tinyply PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/source>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/third-party>
)
