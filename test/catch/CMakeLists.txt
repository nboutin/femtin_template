##### Configuration

cmake_minimum_required(3.0.0)
project(project_unittest)

##### 3rd party

# Prepare "Catch" library for other executables
set(CATCH_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/catch)
add_library(Catch INTERFACE)
target_include_directories(Catch INTERFACE ${CATCH_INCLUDE_DIR})

##### Include

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inc)

##### Source

set(source
	${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/src/test_template.cpp
)

##### Compilation

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

##### Target

add_executable(${PROJECT_NAME} ${source})

target_link_libraries(
	${PROJECT_NAME}
	Catch
)

##### install(

install(TARGETS ${PROJECT_NAME} DESTINATION ${TO_BE_DEFINED})

