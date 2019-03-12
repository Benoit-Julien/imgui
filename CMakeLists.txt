cmake_minimum_required(VERSION 3.8)
project(Imgui)

set(CMAKE_CXX_STANDARD 11)

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
target_link_libraries(imgui ${LIBRARIES})
target_compile_definitions(imgui PRIVATE IMGUI_IMPL_OPENGL_LOADER_GLEW)