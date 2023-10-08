#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

# AC_PREREQ([2.71])
AC_INIT([TestU01],[1.2.3],[lecuyer@iro.umontreal.ca])
AC_CONFIG_SRCDIR([mylib/num.c])
AM_INIT_AUTOMAKE
AC_CONFIG_HEADERS([include/config.h])
AC_CONFIG_HEADERS([include/gdefconf.h])

AC_CANONICAL_HOST

# Checks for programs.
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET
LT_INIT
AC_CHECK_PROG(have_mathematica,math, yes, no) 
if test "x$have_mathematica" = "xyes" ; then
   AC_DEFINE([HAVE_MATHEMATICA], 1, [Define when Mathematica is installed])
fi

# Checks for libraries.
LT_LIB_M

# Checks for header files.
m4_warn([obsolete],
[The preprocessor macro `STDC_HEADERS' is obsolete.
  Except in unusual embedded environments, you can safely include all
  ISO C90 headers unconditionally.])dnl
# Autoupdate added the next two lines to ensure that your configure
# script's behavior did not change.  They are probably safe to remove.
AC_CHECK_INCLUDES_DEFAULT
AC_PROG_EGREP

AC_CHECK_HEADERS([sys/utsname.h unistd.h windows.h gmp.h stdint.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_TYPE_SIZE_T
AC_C_BIGENDIAN
AC_CHECK_TYPES([long long, uint32_t, uint8_t])

# Checks for library functions.
# AC_FUNC_MALLOC
# AC_FUNC_REALLOC
LIBS="$LIBM $LIBS"
AC_CHECK_FUNCS([random erf lgamma log1p])

AC_CONFIG_FILES([Makefile
                 include/Makefile mylib/Makefile probdist/Makefile
                 testu01/Makefile examples/Makefile doc/Makefile param/Makefile])
AC_SUBST([LIBM])
AC_OUTPUT
