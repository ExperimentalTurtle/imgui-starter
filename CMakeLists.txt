cmake_minimum_required(VERSION 3.22)
project(first_imgui)

set(CMAKE_CXX_STANDARD 14)

add_executable(first_imgui glad.c main.cpp)
#add_executable(first_imgui main.cpp)


find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

include_directories( ${OPENGL_INCLUDE_DIRS}  ${GLUT_INCLUDE_DIRS} )
target_link_libraries(first_imgui ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} GL dl glfw)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)