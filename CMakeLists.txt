cmake_minimum_required(VERSION 3.14)

project(TestU01 LANGUAGES C)

macro(target_generate_headers target_name)
    foreach(header_name IN ITEMS ${ARGN})
        add_custom_command(
            OUTPUT "${header_name}.h"
            COMMAND tcode "${CMAKE_CURRENT_LIST_DIR}/${header_name}.tex" "${header_name}.h"
            DEPENDS "${CMAKE_CURRENT_LIST_DIR}/${header_name}.tex"
            COMMENT "Generating ${header_name}.h"
            VERBATIM)
        target_sources(${target_name} PRIVATE "${header_name}.h")
    endforeach()

    target_include_directories(${target_name} PUBLIC ${CMAKE_CURRENT_BINARY_DIR})
endmacro()

include(CTest)

add_subdirectory(include)
add_subdirectory(mylib)
add_subdirectory(probdist)
add_subdirectory(testu01)
add_subdirectory(config)
add_subdirectory(examples)
