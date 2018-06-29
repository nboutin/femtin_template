##### Configuration

cmake_minimum_required(3.0.0)
project(project_template)

##### 3rd party

find_package(PkgConfig REQUIRED)

pkg_check_modules(MODULE_EXT REQUIRED
	# module_name
)

##### Include

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inc)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/interface)

##### Source

set(source
	${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
)

##### Compilation

# Switch
add_definitions(${MODULE_EXT_CFLAGS})

# Flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

##### Target

# executable
add_executable(${PROJECT_NAME} ${source})

# library
add_library (${PROJECT_NAME} SHARED ${sources})

target_link_libraries (${PROJECT_NAME} ${MODULE_EXT_LDFLAGS})

set_target_properties (${PROJECT_NAME} PROPERTIES
	VERSION ${DB_MANAGER_VERSION}
  	SOVERSION ${DB_MANAGER_VERSION}
)

##### Install

# executable
install(${PROJECT_NAME})

# library

install (TARGETS ${PROJECT_NAME} LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})

install(
  FILES
  ${CMAKE_CURRENT_SOURCE_DIR}/interface/interface_template.h
  DESTINATION ${TO_BE_DEFINED}
  PERMISSIONS OWNER_WRITE OWNER_READ GROUP_READ WORLD_READ
)

# Pkgconfig
configure_file (
    ${PROJECT_NAME}.pc.in
    ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}/${PROJECT_NAME}.pc
    @ONLY
)

install(
    FILES ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}/${PROJECT_NAME}.pc
    DESTINATION ${TO_BE_DEFINED}
    PERMISSIONS OWNER_WRITE OWNER_READ GROUP_READ WORLD_READ
)