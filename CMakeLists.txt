cmake_minimum_required(VERSION 3.10)
project(submodule-3.1)

enable_testing()

# Create a library that can be linked against
add_library(submodule31_lib submodule31.c)

# Create the executable with a different name
add_executable(submodule31 submodule31.c)

# Add Google Test
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

# Compile test executable
add_executable(test-submodule31 test-submodule31.cpp)
target_link_libraries(test-submodule31 GTest::GTest GTest::Main pthread submodule31_lib)

# Register test with CTest
add_test(NAME submodule3_1_test COMMAND test-submodule31)

# Make the library target available to parent projects
set_target_properties(submodule31_lib PROPERTIES EXPORT_NAME submodule31_lib)
