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

createdb = \
	$(IBUS_TABLE_CREATEDB) 

if IBUS_TABLE_EXTRA_PHRASES
createdb += -e @IBUS_TABLE_EXTRAPHRASE@
endif

tables_DATA = taiji.txt

tables_DATA += $(NULL)

tablesdir = $(datadir)/ibus-table/tables

EXTRA_DIST = $(tables_DATA)  \
	$(NULL)

DISTCLEANFILES = \
	*.db \
	$(NULL)

.txt.db:
	$(createdb) -n $@ -s $<

