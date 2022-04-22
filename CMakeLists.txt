cmake_minimum_required(VERSION 3.22)
project(first_imgui)

set(CMAKE_CXX_STANDARD 14)
set(LIB_DIR "${CMAKE_CURRENT_SOURCE_DIR}/lib")

add_executable(first_imgui glad.c main.cpp)

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

include_directories(${OPENGL_INCLUDE_DIRS} ${GLUT_INCLUDE_DIRS})

target_link_libraries(
        first_imgui
        ${OPENGL_LIBRARIES}
        ${CMAKE_DL_LIBS}
        glfw
)

# glfw
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)


#imgui
set(IMGUI_DIR "${LIB_DIR}/imgui")
add_library("imgui" "${IMGUI_DIR}/imgui.cpp"
        "${IMGUI_DIR}/imgui_demo.cpp"
        "${IMGUI_DIR}/imgui_draw.cpp"
        "${IMGUI_DIR}/imgui_tables.cpp"
        "${IMGUI_DIR}/imgui_widgets.cpp"

        "${IMGUI_DIR}/imgui_impl_glfw.cpp"
        "${IMGUI_DIR}/imgui_impl_opengl3.cpp")
target_include_directories("imgui" PRIVATE "${IMGUI_DIR}")
target_include_directories(${PROJECT_NAME} PRIVATE "${IMGUI_DIR}")
target_link_libraries(${PROJECT_NAME} "imgui" "${CMAKE_DL_LIBS}")