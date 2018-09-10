##### Configuration

cmake_minimum_required(VERSION 3.0.0)
project(comp_name)

##### 3rd party

find_package(PkgConfig REQUIRED)

pkg_check_modules(MODULE_EXT REQUIRED
	# module_name
)

##### Include

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inc)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/interface)	#delete if not library

##### Source

set(SOURCE
	${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/src/template.cpp
)

##### Compilation

# Switch
add_definitions(${MODULE_EXT_CFLAGS})

# Flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

##### Target

# DELETE ME: choose between 1-executable or 2-library

# 1-executable
add_executable(${PROJECT_NAME} ${SOURCE})

target_link_libraries (
    ${PROJECT_NAME}
    ${MODULE_EXT_LDFLAGS}
)

# 2-library
add_library (${PROJECT_NAME} SHARED ${SOURCE})

target_link_libraries (${PROJECT_NAME} ${MODULE_EXT_LDFLAGS})

# DELETE ME: COMPONENT_VERSION is define in the yocto recipe
set_target_properties (${PROJECT_NAME} PROPERTIES
	VERSION ${COMPONENT_VERSION}
  	SOVERSION ${COMPONENT_VERSION}
)

##### Install

# DELETE ME: choose between 1-executable or 2-library

# 1-executable
install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})

# 2-library

install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})

install(
  FILES
  ${CMAKE_CURRENT_SOURCE_DIR}/interface/interface_template.h
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}
  PERMISSIONS OWNER_WRITE OWNER_READ GROUP_READ WORLD_READ
)

# Pkgconfig
configure_file (
    ${CMAKE_CURRENT_SOURCE_DIR}/${PROJECT_NAME}.pc.in
    ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}/${PROJECT_NAME}.pc
    @ONLY
)

install(
    FILES ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}/${PROJECT_NAME}.pc
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/pkgconfig
    PERMISSIONS OWNER_WRITE OWNER_READ GROUP_READ WORLD_READ
)