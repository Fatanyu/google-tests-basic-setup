# google-tests-basic-setup

## notes for prep CLion version (it is a little different than this repository)
```
### prepare directories for google tests
mkdir -p external-libraries/google-tests
cd external-libraries/google-tests
### we need CMakeList.txt just for git to track external-libraries/google-tests (without it git submodule fail)
touch CMakeList.txt
git submodule add git@github.com:google/googletest.git #or another address

cd ../.. #project root

### modify project CMakeList.txt
echo "add_subdirectory(external-libraries/google-tests)" >> CMakeList.txt
echo "include_directories(external-libraries/google-tests/googletest/googletest/include)" >> CMakeList.txt
echo "include_directories(external-libraries/google-tests/googletest/googlemock/include)" >> CMakeList.txt

echo "
cmake_minimum_required(VERSION 3.15)
# 'Google_test' is the subproject name
project(google-tests)

# 'lib' is the folder with Google Test sources
add_subdirectory(googletest)


include_directories(${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})

include_directories(../../sources)

# 'Google_Tests_run' is the target name
# 'test1.cpp tests2.cpp' are source files with tests
#add_executable(Google_Tests_run test1.cpp tests2.cpp) ### original file
add_executable(google-tests-run dummy-test.cpp) ### put here all test files

target_link_libraries(google-tests-run gtest gtest_main)" > ./external-libraries/google-tests/CMakeList.txt

echo "#include <gtest/gtest.h>

TEST(DummyTest, HelloWorld)
{
    //always true; When this test do not pass, you need to check configuration
    ASSERT_EQ(true, true);
}" > ./external-libraries/google-tests/dummy-test.cpp

## Edit configuration
## > find google test and click create configuration
## > switch to Target: google-tests-run
## > save
## try to run it```
