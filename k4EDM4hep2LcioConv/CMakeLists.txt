add_library(k4EDM4hep2LcioConv SHARED
  src/k4EDM4hep2LcioConv.cpp)

target_include_directories(k4EDM4hep2LcioConv PUBLIC
  ${LCIO_INCLUDE_DIRS}
  $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/include>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)

target_link_libraries(k4EDM4hep2LcioConv PUBLIC
  ${LCIO_LIBRARIES}
  EDM4HEP::edm4hep)

set_target_properties(${CMAKE_PROJECT_NAME}
  PROPERTIES
  PUBLIC_HEADER "include/${CMAKE_PROJECT_NAME}/k4EDM4hep2LcioConv.h")

install(TARGETS k4EDM4hep2LcioConv
  EXPORT ${CMAKE_PROJECT_NAME}Targets
  RUNTIME DESTINATION "${CMAKE_INSTALL_BINDIR}" COMPONENT bin
  LIBRARY DESTINATION "${CMAKE_INSTALL_LIBDIR}" COMPONENT shlib
  PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/${CMAKE_PROJECT_NAME}"
  COMPONENT dev)
