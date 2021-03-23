cmake_minimum_required(VERSION 3.9)

project("blkmaker")

set(SOURCE_FILES
    base58.c
    blkmaker.c
    blkmaker.h
    blkmaker_jansson.c
    blkmaker_jansson.h
    blktemplate.c
    blktemplate.h
    test.c
    testinput.c
    hex.c
    private.h
)

include_directories(${CMAKE_CURRENT_LIST_DIR})

add_library("blkmaker" SHARED ${SOURCE_FILES})

target_link_libraries("blkmaker" PUBLIC jansson base58)

add_executable("example" "example.c")

target_link_libraries("example" PUBLIC "blkmaker" gcrypt)

