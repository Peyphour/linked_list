cmake_minimum_required(VERSION 3.9)
project(linked_list LANGUAGES C VERSION 1.0 DESCRIPTION "multi purpose linked list")
include(GNUInstallDirs)

set(CMAKE_C_STANDARD 11)


add_library(linked_list SHARED linked_list.c linked_list.h)

set_target_properties(linked_list PROPERTIES
        VERSION ${PROJECT_VERSION}
        SOVERSION 1
        PUBLIC_HEADER linked_list.h)
configure_file(linked_list.pc.in linked_list.pc @ONLY)
target_include_directories(linked_list PRIVATE .)
install(TARGETS linked_list
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(FILES ${CMAKE_BINARY_DIR}/linked_list.pc
        DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)