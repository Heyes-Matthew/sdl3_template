cmake_minimum_required(VERSION 3.15)

project(sdl3_template
    VERSION 0.0.0
    DESCRIPTION "SDL3 template project targetting Windows and Linux"
    LANGUAGES C CXX
)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Set up SDL
add_subdirectory(build/vendored/SDL EXCLUDE_FROM_ALL)
set(SDL3_LIBRARY SDL3)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/bin")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/lib")

add_executable(${PROJECT_NAME} src/main.c)

target_link_libraries(${PROJECT_NAME} PRIVATE ${SDL3_LIBRARY})