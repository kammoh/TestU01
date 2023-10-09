add_executable(tcode tcode.c)
target_link_libraries(tcode PUBLIC testu01_include)

add_library(testu01_mylib OBJECT)

set_target_properties(testu01_mylib PROPERTIES C_STANDARD 99)

target_link_libraries(testu01_mylib PUBLIC testu01_include)

target_generate_headers(testu01_mylib
	gdef
	addstr
	bitset
	chrono
	mystr
	num
	num2
	tables
	util)

target_sources(testu01_mylib PRIVATE
	gdef.c
	addstr.c
	bitset.c
	chrono.c
	mystr.c
	num.c
	num2.c
	tables.c
	util.c)
