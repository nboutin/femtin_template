##### Configuration

cmake_minimum_required(VERSION 3.0.0)
project(example_template)

##### 3rd party

##### Include

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inc)

##### Source

set(SOURCE
	${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
)

##### Compilation

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

##### Target

add_executable(${PROJECT_NAME} ${SOURCE})

target_link_libraries(
	${PROJECT_NAME}
	#lib_name
)

##### Install

install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION ${EXAMPLE_PATH})