##### Configuration

cmake_minimum_required(3.0.0)

set(RUNTIME_OUTPUT_DIRECTORY output/bin)
set(LIBRARY_OUTPUT_DIRECTORY output/bin)

##### Source

add_subdirectory(source)

add_subdirectory(example/example_template)

add_subdirectory(test/catch)