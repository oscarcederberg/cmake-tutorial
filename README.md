# CMake Tutorial
Following [CMake Guides](https://cmake.org/cmake/help/latest/index.html#guides).

## 01 Build and Run
Create a build directory, set it up with CMake, and build the project.
```bash
mdkir build
cd build
cmake ..
cmake --build . # Can be run from root-, or build-directory
```

## 02 Version Number and Config Header File
Variables included in the _CMakeLists.txt_:

* `${PROJECT_NAME}` is the project name specified in the latest `project()`-command.
* `${CMAKE_PROJECT_NAME}` is the top-level project name specified in the latest `project()`-command from the top-level _CMakeLists.txt_.
* `${PROJECT_BINARY_DIR}` returns the build directory of the project. `CMAKE_` is for top-level _CMakeLists.txt_ build directory.
* `${PROJECT_SOURCE_DIR}` returns the root directory of the project. `CMAKE_` is for top-level _CMakeLists.txt_ root directory.

`configure_file()` will automatically output the new header into the build-directory (`${PROJECT_BINDARY_DIR}`) if a relative path is used. You can set an absolute path by setting output to e.g. `"${PROJECT_SOURCE_DIR}/include/<file_name>"`.\
In `target_include_directories()`, the directory can be changed to `${PROJECT_BINARY_DIR}` if relative path was used for config file. Relative path will be based on root of project directory, not build-directory.

## 03 C++ Standard
`set(CMAKE_CXX_STANDARD_REQUIRED True)` is required for the `CXX_STANDARD`-property not to risk decaying to a previous standard.

## 04 Add a library
It is possible to add `libs/CMakeLists.txt` with `add_subdirectory(ExampleLib)` and then add `libs` as a subdirectory to root instead. However, it makes is a bit more puzzling to handle optional libraries.

## 05 Add Usage Requirements
The usage requirement in `target_include_directories()` states who needs include the current source directory.

* `INTERFACE`: consumers, but not the producer.
* `PRIVATE`: producer, but not the consumers.
* `PUBLIC`: both consumers and producer.