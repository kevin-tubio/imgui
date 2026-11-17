cmake_minimum_required(VERSION 3.22.1)

set(PROJECT_NAME ImGui)
project(${PROJECT_NAME} LANGUAGES CXX)

add_library(${PROJECT_NAME} STATIC
        imgui.cpp
        imgui_draw.cpp
        imgui_tables.cpp
        imgui_widgets.cpp
        imgui_demo.cpp
        backends/imgui_impl_glfw.cpp
        backends/imgui_impl_opengl3.cpp
)

target_include_directories(${PROJECT_NAME} PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
        "${CMAKE_CURRENT_SOURCE_DIR}/backends"
)

find_package(OpenGL REQUIRED)
target_link_libraries(${PROJECT_NAME} PUBLIC glfw OpenGL::GL)
