add_definitions(
  -D_FILE_OFFSET_BITS=64
)

SET(fsalceph_LIB_SRCS
   main.c
   export.c
   handle.c
   mds.c
   ds.c
   internal.c
   internal.h
)

add_library(fsalceph SHARED ${fsalceph_LIB_SRCS})

target_link_libraries(fsalceph cephfs ${SYSTEM_LIBRARIES})

set_target_properties(fsalceph PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS fsalceph COMPONENT fsal DESTINATION ${FSAL_DESTINATION} )
