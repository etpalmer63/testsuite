##============================================================================
##  Copyright (c) Kitware, Inc.
##  All rights reserved.
##  See LICENSE.txt for details.
##
##  This software is distributed WITHOUT ANY WARRANTY; without even
##  the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
##  PURPOSE.  See the above copyright notice for more information.
##============================================================================

cmake_minimum_required(VERSION 3.12...3.15 FATAL_ERROR)
project(VTKmSmokeTest CXX)
include(CTest)

find_package(VTKm REQUIRED)

add_executable(smoke_test smoke_test.cxx)
target_link_libraries(smoke_test PRIVATE vtkm_source)
vtkm_add_target_information(smoke_test
                            DROP_UNUSED_SYMBOLS MODIFY_CUDA_FLAGS
                            DEVICE_SOURCES smoke_test.cxx)

add_test(NAME SmokeTestInternal COMMAND ${CMAKE_BINARY_DIR}/smoke_test)
