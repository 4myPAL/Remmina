# remmina-plugin-gtk - The GTK+ Remote Desktop Client
#
# Copyright (C) 2011 Marc-Andre Moreau
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, 
# Boston, MA 02111-1307, USA.

set(CMAKE_THREAD_PREFER_PTHREAD)
find_package(Threads)

set(REMMINA_PLUGIN_RDP_SRCS
	remminapluginrdp.c
	remminapluginrdp.h
	remminapluginrdpui.c
	remminapluginrdpui.h
	remminapluginrdpev.c
	remminapluginrdpev.h
	remminapluginrdpfile.c
	remminapluginrdpfile.h
	remminapluginrdpset.c
	remminapluginrdpset.h
	)

add_library(remmina-plugin-rdp ${REMMINA_PLUGIN_RDP_SRCS})
set_target_properties(remmina-plugin-rdp PROPERTIES PREFIX "")

include_directories(${REMMINA_COMMON_INCLUDE_DIRS} ${FREERDP_INCLUDE_DIRS})
target_link_libraries(remmina-plugin-rdp ${REMMINA_COMMON_LIBRARIES} ${FREERDP_LIBRARIES})

install(TARGETS remmina-plugin-rdp DESTINATION ${REMMINA_PLUGINDIR})

