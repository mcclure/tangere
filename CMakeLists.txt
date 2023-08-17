
################################################################################
#  Copyright 2009, 2010 Grove City College
#
#  Licensed under the Apache License, Version 2.0 (the "License");
#  you may not use this file except in compliance with the License.
#  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.
#


################################################################################
# tangere distributable

PROJECT(tangere-dist)

CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

SET(CMAKE_VERBOSE_MAKEFILE ON)

# The following lines break modern MSVC.
if (MSVC)
else (MSVC)
 # This line ought to work in MSVC and it is worrisome it does not.
 SET(BUILD_SHARED_LIBS ON)
 # These are not modern CMake idiomatic, the files should be built in place then moved in an install step.
 SET(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/lib CACHE INTERNAL "Single output directory for building all libraries")
 SET(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin CACHE INTERNAL "Single output directory for building all executables")
endif (MSVC)

INCLUDE_DIRECTORIES(
  ${CMAKE_CURRENT_SOURCE_DIR}
  )

add_subdirectory(Common)
add_subdirectory(tangere)

SET(PASSED_FIRST_CONFIGURE ON CACHE INTERNAL "Already configured once?")
