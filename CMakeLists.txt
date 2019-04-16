cmake_minimum_required(VERSION 3.8)
project(Imgui)

set(CMAKE_CXX_STANDARD 11)

option(OPENGL_LOADER_GL3W "Build shared libraries" OFF)
option(OPENGL_LOADER_GLEW "Build shared libraries" OFF)
option(OPENGL_LOADER_GLAD "Build shared libraries" OFF)

set(SOURCES
        imgui/imgui.cpp
        imgui/imgui_demo.cpp
        imgui/imgui_draw.cpp
        imgui/imgui_widgets.cpp
        imgui/impl/imgui_impl_glfw.cpp
        imgui/impl/imgui_impl_opengl3.cpp
        )

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/imgui)

add_library(imgui STATIC ${SOURCES})

if (OPENGL_LOADER_GL3W)
    message(STATUS "Use gl3w implementation.")
    target_compile_definitions(imgui PRIVATE IMGUI_IMPL_OPENGL_LOADER_GL3W)
elseif (OPENGL_LOADER_GLEW)
    message(STATUS "Use glew implementation.")
    target_compile_definitions(imgui PRIVATE IMGUI_IMPL_OPENGL_LOADER_GLEW)
elseif (OPENGL_LOADER_GLAD)
    message(STATUS "Use glad implementation.")
    target_compile_definitions(imgui PRIVATE IMGUI_IMPL_OPENGL_LOADER_GLAD)
endif ()