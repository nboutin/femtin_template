##### Configuration

cmake_minimum_required(VERSION 3.0.0)
project(comp_name_unittest_catch)

##### 3rd party

# Prepare "Catch" library for other executables
set(CATCH_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/catch)
add_library(Catch INTERFACE)
target_include_directories(Catch INTERFACE ${CATCH_INCLUDE_DIR})

##### Include

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inc)

##### Source

set(SOURCE
	${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/src/test_template.cpp
)

##### Compilation

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

##### Target

add_executable(${PROJECT_NAME} ${SOURCE})

target_link_libraries(
	${PROJECT_NAME}
	Catch
)

##### install

# DELETE ME: INSTALL_TEST_PATH define in recipe
install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION ${OSS_TEST_UNIT_PATH})

