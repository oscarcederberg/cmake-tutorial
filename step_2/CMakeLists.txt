cmake_minimum_required(VERSION 3.10)
project(Tutorial VERSION 1.0)

configure_file(TutorialConfig.h.in "${PROJECT_SOURCE_DIR}/include/TutorialConfig.h")

add_executable("${PROJECT_NAME}" tutorial.cpp)

target_include_directories("${PROJECT_NAME}" PUBLIC
	"include"
	)
