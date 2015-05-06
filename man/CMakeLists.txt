# Search for gzip program
INCLUDE (FindGZIP.cmake)

# Lists of source manuals
SET(roof_man_src_3 btree.3
	dbopen.3
	mpool.3
	recno.3)

# Lists of compressed manuals
STRING(REGEX REPLACE ".3" ".3.gz" roof_man_gz_3 "${roof_man_src_3}")


# Compression of the manuals
FOREACH(man ${roof_man_src_3} )
	ADD_CUSTOM_COMMAND(OUTPUT ${man}.gz
		COMMAND ${GZIP_TOOL} -c ${man} > ${man}.gz
		DEPENDS ${man}
		COMMENT "Building ${man}.gz")
ENDFOREACH(man)

# Add the manual generation in the global rules
ADD_CUSTOM_TARGET(man ALL
	DEPENDS ${roof_man_gz_3})

# Installation of the manuals
INSTALL(FILES ${roof_man_gz_3}
	DESTINATION "share/man/man3"
	PERMISSIONS OWNER_READ GROUP_READ WORLD_READ)
