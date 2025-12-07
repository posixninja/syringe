AC_PREREQ([2.69])
AC_INIT([syringe], [0.1], [https://github.com/chronic-dev/syringe/issues], [syringe])
AC_CONFIG_SRCDIR([syringe/libirecovery.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIRS([m4])
AM_INIT_AUTOMAKE([foreign subdir-objects])
AM_SILENT_RULES([yes])

AC_PROG_CC
AM_PROG_AR

PKG_PROG_PKG_CONFIG
PKG_CHECK_MODULES([LIBUSB], [libusb-1.0])
PKG_CHECK_MODULES([LIBCURL], [libcurl])

AC_CHECK_HEADERS([zlib.h], [], [AC_MSG_ERROR([zlib.h is required but was not found])])
AC_CHECK_LIB([z], [inflate], [ZLIB_LIBS="-lz"], [AC_MSG_ERROR([zlib library not found])])
AC_SUBST([ZLIB_LIBS])

AC_ARG_VAR([ARM_AS], [Assembler used when building DFU payloads])
AC_ARG_VAR([ARM_OBJCOPY], [objcopy used when building DFU payloads])
AC_ARG_VAR([ARM_ASFLAGS], [Assembler flags for DFU payloads])
AC_ARG_VAR([ARM_OBJCOPYFLAGS], [objcopy flags for DFU payloads])
AC_ARG_VAR([XXD], [xxd program used to convert payload binaries into headers])

: ${ARM_AS="arm-elf-as"}
: ${ARM_OBJCOPY="arm-elf-objcopy"}
: ${ARM_ASFLAGS="-mthumb"}
: ${ARM_OBJCOPYFLAGS="-O binary"}

AC_SUBST([ARM_AS])
AC_SUBST([ARM_OBJCOPY])
AC_SUBST([ARM_ASFLAGS])
AC_SUBST([ARM_OBJCOPYFLAGS])

AC_PATH_PROG([XXD], [xxd])
if test -z "$XXD"; then
  AC_MSG_ERROR([xxd is required to build the payload headers])
fi

AC_CONFIG_FILES([
Makefile
include/Makefile
syringe/Makefile
utilities/Makefile
])
AC_OUTPUT
