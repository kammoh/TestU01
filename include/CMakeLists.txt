include(CheckIncludeFile)
include(CheckSymbolExists)
include(CheckTypeSize)

check_include_file(dlfcn.h HAVE_DLFCN_H)
check_include_file(gmp.h HAVE_GMP_H)
check_include_file(inttypes.h HAVE_INTTYPES_H)
check_include_file(memory.h HAVE_MEMORY_H)
check_include_file(stddef.h HAVE_STDDEF_H)
check_include_file(stdint.h HAVE_STDINT_H)
check_include_file(stdlib.h HAVE_STDLIB_H)
check_include_file(string.h HAVE_STRING_H)
check_include_file(strings.h HAVE_STRINGS_H)
check_include_file(sys/stat.h HAVE_SYS_STAT_H)
check_include_file(sys/types.h HAVE_SYS_TYPES_H)
check_include_file(sys/utsname.h HAVE_SYS_UTSNAME_H)
check_include_file(unistd.h HAVE_UNISTD_H)
check_include_file(windows.h HAVE_WINDOWS_H)

unset(HAVE_LEBOOL)
check_type_size("long long" LONG_LONG BUILTIN_TYPES_ONLY LANGUAGE C)
check_type_size("uint32_t" UINT32_T LANGUAGE C)
check_type_size("uint8_t" UINT8_T LANGUAGE C)

check_symbol_exists(random "stdlib.h" HAVE_RANDOM)

set(CMAKE_REQUIRED_LIBRARIES m)
check_symbol_exists(erf "math.h" HAVE_ERF)
check_symbol_exists(lgamma "math.h" HAVE_LGAMMA)
check_symbol_exists(log1p "math.h" HAVE_LOG1P)

set(PACKAGE "testu01")
set(PACKAGE_BUGREPORT "lecuyer@iro.umontreal.ca")
set(PACKAGE_NAME "TestU01")
set(PACKAGE_STRING "TestU01 1.2.3")
set(PACKAGE_TARNAME "testu01")
set(PACKAGE_VERSION "1.2.3")
set(STDC_HEADERS ON)
set(VERSION "1.2.3")

if(CMAKE_C_BYTE_ORDER STREQUAL BIG_ENDIAN)
    set(WORDS_BIGENDIAN ON)
else()
    set(WORDS_BIGENDIAN OFF)
endif()

unset(CONST)
unset(SIZE_T)

configure_file(gdefconf_cmake.h.in gdefconf.h @ONLY)
configure_file(config_cmake.h.in config.h @ONLY)

add_library(testu01_include INTERFACE)
target_compile_definitions(testu01_include INTERFACE HAVE_CONFIG_H)
target_include_directories(testu01_include INTERFACE ${CMAKE_CURRENT_BINARY_DIR})
if(WIN32)
  target_compile_definitions(testu01_include INTERFACE _CRT_SECURE_NO_WARNINGS)
endif()

include(CheckLibraryExists)
check_library_exists(m pow "" LIBM_FOUND)
if(LIBM_FOUND)
    target_link_libraries(testu01_include INTERFACE m)
endif()

# TODO(cwasser): Not supported:
# HAVE_MATHEMATICA
