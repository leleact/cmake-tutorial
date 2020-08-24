cmake_minimum_required(VERSION 2.8.12.2)

project(cmake-tutorial-add_custom_command C CXX)

add_custom_command(OUTPUT hello.txt
	COMMAND ${CMAKE_COMMAND} -E touch hello.txt
	WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
	COMMENT "Generate hello.txt")

add_custom_target(foo_target DEPENDS hello.txt)

add_executable(main main.cpp)
add_dependencies(main foo_target)
