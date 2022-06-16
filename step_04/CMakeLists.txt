cmake_minimum_required(VERSION 3.10)
project(Tutorial VERSION 1.0)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)
option(USE_EXAMPLELIB "Use example lib implementation" ON)

configure_file(TutorialConfig.h.in TutorialConfig.h)

if(USE_EXAMPLELIB)
	add_subdirectory(libs/ExampleLib)
	list(APPEND EXTRA_LIBS ExampleLib)
	list(APPEND EXTRA_INCLUDES "${PROJECT_SOURCE_DIR}/libs/ExampleLib")
endif()

add_executable("${PROJECT_NAME}" tutorial.cpp)

target_link_libraries("${PROJECT_NAME}" PUBLIC ${EXTRA_LIBS})

target_include_directories("${PROJECT_NAME}" PUBLIC
	"${PROJECT_BINARY_DIR}"
	${EXTRA_INCLUDES}
	)
