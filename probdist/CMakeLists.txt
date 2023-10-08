add_library(probdist)
target_link_libraries(probdist PUBLIC testu01_include mylib)
target_generate_headers(probdist
	fmass
	fdist
	fbar
	finv
	gofs
	gofw
	statcoll
	wdist)
target_sources(probdist PRIVATE
	fmass.c
	fdist.c
	fbar.c
	finv.c
	gofs.c
	gofw.c
	statcoll.c
	wdist.c)
