cmake_minimum_required(VERSION 3.2)
project(cxxmetrics)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake")
set(CMAKE_CONFIGURATION_TYPES "Debug" "Release" "Coverage")
set(CMAKE_CXX_FLAGS_COVERAGE
        "-g -O0 --coverage -fprofile-arcs -ftest-coverage"
        CACHE STRING "Flags used by the C++ compiler during coverage builds."
        FORCE
)

if("${CMAKE_BUILD_TYPE}" STREQUAL "Coverage")
    link_libraries(gcov)
endif()

add_subdirectory(src)
add_subdirectory(test)
