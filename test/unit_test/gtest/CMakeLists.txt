##### Configuration

cmake_minimum_required(VERSION 3.0.0)
project(comp_name_gtest)

##### 3rd party

find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})
enable_testing()

find_package(PkgConfig)

pkg_check_modules(MODULE_EXT REQUIRED automotive-dlt)

##### Include

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inc)

# DELETE ME: if testing a library
include_directories(${CMAKE_SOURCE_DIR}/source/interface)

##### Source

set(SOURCE 
	${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/src/test_template.cpp
)

##### Compilation

# Switch
add_definitions(${MODULE_EXT_CFLAGS})

# Flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

##### Target

add_executable(${PROJECT_NAME} ${SOURCE})

target_link_libraries(
	${PROJECT_NAME} 
	pthread 
	${GTEST_BOTH_LIBRARIES}
	${MODULE_EXT_LDFLAGS}
	# DELETE ME: if testing a library
	comp_name
)
	
##### Install

# DELETE ME: OSS_TEST_UNIT_PATH define in recipe
install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION ${TEST_UNIT_PATH})
