cmake_minimum_required(VERSION 3.16)
project(mayhem-cmake-example)

add_executable(fuzzme fuzzme.c)

## Uncomment these lines after converting fuzzme.c into a libFuzzer target
if (NOT CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
    message(FATAL_ERROR "Clang is required for libFuzzer!")
endif()
target_compile_options(fuzzme PUBLIC -fsanitize=fuzzer)
target_link_options(fuzzme PUBLIC -fsanitize=fuzzer)

