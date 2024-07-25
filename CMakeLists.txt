cmake_minimum_required(VERSION 3.11)
project(splinterdb LANGUAGES C)
set(CMAKE_C_FLAGS "-g -O2 -D_GNU_SOURCE -ggdb -Wall -pthread -Wvla -DXXH_STATIC_LINKING_ONLY -fPIC -march=native")

file(GLOB SOURCES "src/*.c")
file(GLOB PLATFORM "src/platform_linux/*.c")

add_library(splinterdb ${SOURCES} ${PLATFORM})
target_include_directories(splinterdb PUBLIC include src)
target_include_directories(splinterdb PUBLIC src/platform_linux)
target_link_libraries(splinterdb PUBLIC xxhash)
