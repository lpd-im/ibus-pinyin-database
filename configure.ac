# vim:set et ts=4:
#
# ibus-pinyin - The Chinese PinYin engine for IBus
#
# Copyright (c) 2007-2008 Peng Huang <shawn.p.huang@gmail.com>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

# if not 1, append datestamp to the version number.
m4_define([ibus_released], [0])
m4_define([ibus_major_version], [1])
m4_define([ibus_minor_version], [2])
m4_define([ibus_micro_version], [99])
m4_define(ibus_maybe_datestamp,
    m4_esyscmd([if test x]ibus_released[ != x1; then date +.%Y%m%d | tr -d '\n\r'; fi]))

m4_define([ibus_version],
    ibus_major_version.ibus_minor_version.ibus_micro_version[]ibus_maybe_datestamp)

AC_INIT([ibus-pinyin-database], [ibus_version], [http://code.google.com/p/ibus/issues/entry],[ibus-pinyin-database])
AM_INIT_AUTOMAKE([1.10])
# AC_GNU_SOURCE

AC_CONFIG_MACRO_DIR([m4])

# define PACKAGE_VERSION_* variables
AS_VERSION
AS_NANO
AM_SANITY_CHECK
AM_MAINTAINER_MODE

# check env
AC_PATH_PROG(ENV, env)
AC_SUBST(ENV)

#check python
AM_PATH_PYTHON([2.5])

# define GETTEXT_* variables

# --enable-build-db
AC_ARG_ENABLE(pinyin-database,
    AS_HELP_STRING([--disable-pinyin-database],
        [do not build pinyin database]),
    [enable_pinyin_database=$enableval],
    [enable_pinyin_database=yes]
)
AM_CONDITIONAL(IBUS_BUILD_PINYIN_DATABASE, [test x"$enable_pinyin_database" = x"yes" ])

# OUTPUT files
AC_CONFIG_FILES([
  Makefile
  ibus-pinyin-database.spec
  ibus-pinyin-database-1.0.pc
  data/Makefile
  m4/Makefile
])

AC_OUTPUT

AC_MSG_RESULT([
Build options:
    Version                 $VERSION
    Install prefix          $prefix
])

