#
# This file was taken from RakNet 4.082 without any modifications.
# Please see licenses/RakNet license.txt for the underlying license and related copyright.
#

project(PostgreSQLInterface)
IF (NOT WIN32 AND UNIX)
	FILE(GLOB ALL_HEADER_SRCS *.h)
	FILE(GLOB ALL_CPP_SRCS *.cpp)
	FINDPOSTGRE()
	include_directories(./ ${RAKNETHEADERFILES} ${POSTGRESQL_INCLUDE_DIR}) 
	add_library(LibPostgreSQLInterface STATIC ${ALL_CPP_SRCS} ${ALL_HEADER_SRCS})
	target_link_libraries (LibPostgreSQLInterface ${RAKNET_COMMON_LIBS} ${POSTGRESQL_LIBRARIES})
	VSUBFOLDER(LibPostgreSQLInterface "DependentExtensions")
ENDIF(NOT WIN32 AND UNIX)

