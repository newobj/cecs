# cmake

cmake_minimum_required (VERSION 2.6)
project (cecs)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_FLAGS "-Wall -Wextra -g -fsanitize=alignment,undefined,address")
#set(CMAKE_CXX_FLAGS "-Wall -Wextra -O3")
set(CMAKE_OSX_ARCHITECTURES x86_64)

file(GLOB_RECURSE src
    "cecs/*.cpp"
    "benchmark/*.cpp"
)

# target

add_executable(benchmark ${src})
target_link_libraries(benchmark)
#target_compile_definitions(CVLT PRIVATE "-D_CRT_SECURE_NO_WARNINGS" "-D__STDC_FORMAT_MACROS")
install(TARGETS benchmark DESTINATION bin)
