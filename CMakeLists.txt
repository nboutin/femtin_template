##### Configuration

cmake_minimum_required(VERSION 3.0.0)
project(comp_name)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/output/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/output/lib)

##### Source

add_subdirectory(source)

##### Example

add_subdirectory(example/example_template)
	# add other sub-directory example here

##### Test

add_subdirectory(test/integration_test/gtest)
add_subdirectory(test/unit_test/catch)
add_subdirectory(test/unit_test/gtest)

##### Documentation

add_subdirectory(doc)
