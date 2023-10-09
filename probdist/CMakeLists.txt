add_library(testu01_probdist OBJECT)
set_target_properties(testu01_probdist PROPERTIES C_STANDARD 99)
target_link_libraries(testu01_probdist PUBLIC testu01_include testu01_mylib)
target_include_directories(testu01_probdist PUBLIC ${CMAKE_CURRENT_BINARY_DIR})

target_generate_headers(testu01_probdist
	fmass
	fdist
	fbar
	finv
	gofs
	gofw
	statcoll
	wdist)
target_sources(testu01_probdist PRIVATE
	fmass.c
	fdist.c
	fbar.c
	finv.c
	gofs.c
	gofw.c
	statcoll.c
	wdist.c)
