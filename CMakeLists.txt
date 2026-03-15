cmake_minimum_required(VERSION 3.50)

project(Shooter)

option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)
add_subdirectory("vendor/glfw/")

if(MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /W4")
else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -Wpedantic -std=c++23")
    if(NOT WIN32)
        set(GLAD_LIBRARIES dl)
    endif()
endif()

file(GLOB VENDORS_SOURCES "vendor/glad/src/glad.c")

include_directories("vendor/glfw/include"
                    "vendor/glad/include")

source_group("Shaders" FILES ${PROJECT_SHADERS})

add_executable(Shooter "source/main.cpp")

target_link_libraries(Shooter glfw)
target_include_directories(Shooter PRIVATE "vendor/stb")

add_custom_command(TARGET Shooter POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E copy_directory
                       ${CMAKE_SOURCE_DIR}/resources/ $<TARGET_FILE_DIR:Shooter>/resources)