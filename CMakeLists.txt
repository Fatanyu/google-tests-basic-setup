cmake_minimum_required(VERSION 3.15)
project(google_tests_basic_setup)

set(CMAKE_CXX_STANDARD 20)

add_executable(google_tests_basic_setup source/main.cpp)
add_subdirectory(Google_tests)
include_directories(Google_tests/lib/googletest/googletest/include)
include_directories(Google_tests/lib/googletest/googlemock/include)