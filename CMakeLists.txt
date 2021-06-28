cmake_minimum_required(VERSION 3.19)
project(my_google_test)

set(CMAKE_CXX_STANDARD 20)

# Get Google Test
include(FetchContent)
FetchContent_Declare(
        googletest
        URL https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip
)
FetchContent_MakeAvailable(googletest)

add_executable(main main.cpp)

# Enable Testing
enable_testing()
add_executable(
        hello_test
        hello_test.cc
)
target_link_libraries(
        hello_test
        gtest_main
)
include(GoogleTest)
gtest_discover_tests(hello_test)