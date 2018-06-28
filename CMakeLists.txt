cmake_minimum_required(3.0.0 FATAL_ERROR)

set(RUNTIME_OUTPUT_DIRECTORY output/bin)
set(LIBRARY_OUTPUT_DIRECTORY output/bin)

add_subdirectory(source)

add_subdirectory(example/example_template)

add_subdirectory(test/catch)