add_executable(tcode tcode.c)
target_link_libraries(tcode PUBLIC testu01_include)

add_library(mylib)
target_link_libraries(mylib PUBLIC testu01_include)
target_generate_headers(mylib
	gdef
	addstr
	bitset
	chrono
	mystr
	num
	num2
	tables
	util)
target_sources(mylib PRIVATE
	gdef.c
	addstr.c
	bitset.c
	chrono.c
	mystr.c
	num.c
	num2.c
	tables.c
	util.c)
