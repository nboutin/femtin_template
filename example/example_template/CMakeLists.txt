project(example_template)

include_directories(
	${CMAKE_SOURCE_DIR}/inc
)

set(source
	${CMAKE_SOURCE_DIR}/main.cpp
)

add_executable(${PROJECT_NAME} ${source})

install(${PROJECT_NAME} )