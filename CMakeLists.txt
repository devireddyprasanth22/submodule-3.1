cmake_minimum_required(VERSION 3.10)
project(master-software)

enable_testing() 

# Add Google Test
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

# Compile main program
add_executable(submodule31 submodule31.c)

# Compile test executable
add_executable(test-submodule31 test-submodule31.cpp)
target_link_libraries(test-submodule31 GTest::GTest GTest::Main pthread)

# Register test with CTest
add_test(NAME submodule31 COMMAND test-submodule31)

