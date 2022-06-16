add_library(ExampleLib myfunc.cpp)

target_include_directories(ExampleLib INTERFACE
	${CMAKE_CURRENT_SOURCE_DIR}
	)