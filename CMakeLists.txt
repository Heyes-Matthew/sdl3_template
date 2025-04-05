cmake_minimum_required(VERSION 3.10)

project(sdl3_template)

if(CMAKE_SYSTEM_NAME STREQUAL "Windows")
    set(TARGET_PLATFORM "windows")
else()
    set(TARGET_PLATFORM "linux")
endif()

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/build/${TARGET_PLATFORM})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/build/${TARGET_PLATFORM})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/build/${TARGET_PLATFORM})

add_subdirectory(${CMAKE_BINARY_DIR}/build/vendors/SDL EXCLUDE_FROM_ALL)
add_executable(${PROJECT_NAME} ${CMAKE_SOURCE_DIR}/src/main.c)
target_include_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_SOURCE_DIR}/build/vendors/SDL/include
)
target_link_libraries(${PROJECT_NAME} PRIVATE SDL3::SDL3)

if(TARGET_PLATFORM STREQUAL "windows")
    set_target_properties(${PROJECT_NAME} PROPERTIES SUFFIX ".exe")
else()
    set_target_properties(${PROJECT_NAME} PROPERTIES SUFFIX ".out")
endif()