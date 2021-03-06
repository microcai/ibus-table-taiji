# vim:set ts=4
#
# ibus-table-taiji - The Taiji for IBus Tables.
#
# Copyright (c) 2008-2009 Yu Yuwei <acevery@gmail.com>
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
m4_define([package_name], [ibus-table-taiji])
m4_define([ibus_released], [0])

AC_INIT([package_name], [0.9.9], [http://tjm.taiji1.com/tjminput/index.htm], [package_name])

AM_INIT_AUTOMAKE([1.10])
AM_MAINTAINER_MODE

# AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])

# check python
AM_PATH_PYTHON([2.5])

# check for ibus-table-createdb
PKG_CHECK_MODULES([IBUS_TABLE],[ibus-table >= 1.1.0])

AC_ARG_VAR([IBUS_TABLE_CREATEDB],[[ibus-table-createdb, which generate db]])

AC_PATH_PROG([IBUS_TABLE_CREATEDB],[ibus-table-createdb],
        [AC_MSG_ERROR([ibus-table-createdb not found.])])

# the option for extra phrases
AC_ARG_ENABLE([extra-phrases],
    [AC_HELP_STRING([--enable-extra-phrases],
        [Add extra phrases into built Engine])], ,
    [enable_extra_phrases=no])

AM_CONDITIONAL([IBUS_TABLE_EXTRA_PHRASES],[test x"$enable_extra_phrases" == x"yes"])

# check for ibus-table-extraphrase, if we need it.
if test x"$enable_extra_phrases" == x"yes"; then
    PKG_CHECK_MODULES([EXTRA_PHRASE],[ibus-table-extraphrase >= 1.1.0])
    IBUS_TABLE_EXTRAPHRASE=`$PKG_CONFIG --variable=extraphrasepath ibus-table-extraphrase`
    AC_SUBST(IBUS_TABLE_EXTRAPHRASE)
fi

# OUTPUT files
AC_CONFIG_FILES(Makefile
icons/Makefile
tables/Makefile
)

AC_OUTPUT

AC_MSG_RESULT([
Build options:
  Version                   $VERSION
  Install prefix            $prefix
  Integrate Extra Phrases   $enable_extra_phrases
])

