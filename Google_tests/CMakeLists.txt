cmake_minimum_required(VERSION 3.15)
# 'Google_test' is the subproject name
project(Google_tests)

# 'lib' is the folder with Google Test sources
add_subdirectory(lib/googletest)
include_directories(${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})

# 'Google_Tests_run' is the target name
# 'test1.cpp tests2.cpp' are source files with tests
#add_executable(Google_Tests_run test1.cpp tests2.cpp) ### original file
add_executable(Google_Tests_run ../tests/myTest1.cpp) ### put here all test files
target_link_libraries(Google_Tests_run gtest gtest_main)