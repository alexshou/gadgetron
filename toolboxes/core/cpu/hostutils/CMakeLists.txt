if (WIN32)
  add_definitions(-D__BUILD_GADGETRON_HOSTUTILS__)
endif ()

set(hostutils_scr_files 
    network_utils.cpp
    parameterparser.cpp )

set(hostutils_header_files 
    FileInfo.h
    hostutils_export.h
    network_utils.h
    parameterparser.h
    url_encode.h )

add_library(gadgetron_toolbox_hostutils SHARED 
    ${hostutils_header_files}
    ${hostutils_scr_files}
  )

  target_link_libraries(gadgetron_toolbox_hostutils 
    gadgetron_toolbox_log
    ${Boost_LIBRARIES}
)

set_target_properties(gadgetron_toolbox_hostutils PROPERTIES VERSION ${GADGETRON_VERSION_STRING} SOVERSION ${GADGETRON_SOVERSION})

install(TARGETS 
  gadgetron_toolbox_hostutils 
  DESTINATION lib COMPONENT main)

install(FILES 
  ${hostutils_header_files} 
  DESTINATION ${GADGETRON_INSTALL_INCLUDE_PATH} COMPONENT main)
