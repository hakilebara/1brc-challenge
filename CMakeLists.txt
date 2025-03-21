# Copyright 2021 Arnaud Becheler
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.

cmake_minimum_required(VERSION 3.19)

project(project LANGUAGES CXX)

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")

# add project code
add_subdirectory(src)

# add template project
add_subdirectory(example)

# We default to build tests if option -D CMAKE_BUILD_TESTS=ON not provided (no FORCE, so the previous value, if set, stays)
set(BUILD_TESTS OFF CACHE STRING "Build module test")

if(BUILD_TESTS)
    enable_testing()
    # add unit tests
    add_subdirectory(test)
endif()