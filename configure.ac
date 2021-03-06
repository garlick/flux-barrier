##
# Prologue
##
AC_INIT(m4_esyscmd([awk '/Name:/ {printf "%s",$2; exit}' META]),
        m4_esyscmd([awk '/Version:/ {printf "%s",$2; exit}' META]))
AC_CONFIG_AUX_DIR([config])
AC_CONFIG_SRCDIR([NEWS])
AC_CANONICAL_SYSTEM
X_AC_META
X_AC_EXPAND_INSTALL_DIRS

##
# Automake support
##
AM_INIT_AUTOMAKE([subdir-objects])
AM_SILENT_RULES([yes])
AM_CONFIG_HEADER([config/config.h])
AM_MAINTAINER_MODE

AC_DEFINE([_GNU_SOURCE], 1,
          [Define _GNU_SOURCE so that we get all necessary prototypes])

##
# Checks for programs
##
AC_PROG_CC
AM_PROG_CC_C_O
if test "$GCC" = yes; then
  GCCWARN="-Wall"
  AC_SUBST([GCCWARN])
fi
AC_PROG_RANLIB
AC_PROG_LIBTOOL
AC_CHECK_PROG(A2X,[a2x],[a2x])
if test "$A2X" != "a2x"; then
  AC_MSG_ERROR([Please install asciidoc to get a2x utility.])
fi

##
# Checks for header files.
##
AC_HEADER_STDC
AC_CHECK_HEADERS( \
  pthread.h \
  getopt.h \
)

##
# Checks for typedefs, structures, and compiler characteristics
## 
AC_C_BIGENDIAN
AC_C_CONST

##
# Checks for library functions
##
AC_CHECK_FUNCS( \
  getopt_long \
  vsnprintf \
  vsscanf \
)
X_AC_CHECK_PTHREADS
X_AC_ZEROMQ
X_AC_FLUX_CORE
PKG_CHECK_MODULES(JSON, json)

AC_SYS_LARGEFILE

##
# Epilogue
##
AC_CONFIG_FILES( \
  Makefile \
  flux-barrier.spec \
  src/Makefile \
  src/common/Makefile \
  src/common/libutil/Makefile \
  src/cmd/Makefile \
  src/modules/Makefile \
  src/modules/xbarrier/Makefile \
  doc/Makefile \
  doc/man1/Makefile \
)

AC_OUTPUT
