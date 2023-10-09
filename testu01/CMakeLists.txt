add_library(testu01)

set_target_properties(testu01 PROPERTIES C_STANDARD 99)

target_link_libraries(testu01 testu01_include testu01_mylib testu01_probdist)

set(HEADERS
	unif01
	ulcg
	umrg
	ucarry
	utaus
	ugfsr
	uinv
	uquad
	ucubic
	ulec
	utezuka
	umarsa
	uweyl
	uknuth
	uwu
	unumrec
	uvaria
	usoft
	ugranger
	ucrypto
	ufile
	udeng
	utouzin
	uautomata
	uxorshift
	ubrent
	rijndael-alg-fst
	tu01_sha1
	scatter
	swrite
	sres
	smultin
	sknuth
	smarsa
	sstring
	svaria
	snpair
	swalk
	sentrop
	sspectral
	scomp
	sspacings
	vectorsF2
	bbattery
	ffam
	fcong
	ffsr
	ftab
	fres
	fcho
	fmultin
	fmarsa
	fknuth
	fwalk
	fstring
	fspectral
	fvaria
	fnpair
)

target_generate_headers(testu01 ${HEADERS})

set(HEADERS2 ${HEADERS}
	../mylib/gdef
	../mylib/addstr
	../mylib/bitset
	../mylib/chrono
	../mylib/mystr
	../mylib/num
	../mylib/num2
	../mylib/tables
	../mylib/util
	../probdist/fbar
	../probdist/fdist
	../probdist/finv
	../probdist/fmass
	../probdist/gofs
	../probdist/gofw
	../probdist/statcoll
	../probdist/wdist
	../include/gdefconf)

list(TRANSFORM HEADERS2 APPEND ".h")
list(TRANSFORM HEADERS2 PREPEND "${CMAKE_CURRENT_BINARY_DIR}/")

set_target_properties(
	testu01
	PROPERTIES
	PUBLIC_HEADER "${HEADERS2}"
)

target_sources(testu01 PRIVATE
	unif01.c
	ulcg.c
	umrg.c
	ucarry.c
	utaus.c
	ugfsr.c
	uinv.c
	uquad.c
	ucubic.c
	ulec.c
	utezuka.c
	umarsa.c
	uweyl.c
	uknuth.c
	uwu.c
	unumrec.c
	uvaria.c
	usoft.c
	ugranger.c
	ucrypto.c
	ufile.c
	udeng.c
	utouzin.c
	uautomata.c
	uxorshift.c
	ubrent.c
	rijndael-alg-fst.c
	tu01_sha1.c
	scatter.c
	swrite.c
	sres.c
	smultin.c
	sknuth.c
	smarsa.c
	sstring.c
	svaria.c
	snpair.c
	swalk.c
	sentrop.c
	sspectral.c
	scomp.c
	sspacings.c
	vectorsF2.c
	bbattery.c
	ffam.c
	fcong.c
	ffsr.c
	ftab.c
	fres.c
	fcho.c
	fmultin.c
	fmarsa.c
	fknuth.c
	fwalk.c
	fstring.c
	fspectral.c
	fvaria.c
	fnpair.c
)

install(TARGETS testu01 LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} PUBLIC_HEADER DESTINATION include)