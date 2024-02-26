cmake_minimum_required( VERSION 3.2 )
project(learn_opengl)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(OpenGL REQUIRED)

include_directories(${OpenGL_INCLUDE_DIRS})
include_directories("${CMAKE_SOURCE_DIR}/lib/glad/include")
include_directories("${CMAKE_SOURCE_DIR}/lib")

set(GLFW_BUILD_DOCS OFF CACHE BOOL "GLFW lib only")
set(GLFW_INSTALL OFF CACHE BOOL "GLFW lib only")
set(GLAD_GL "${CMAKE_SOURCE_DIR}/lib/glad")

add_subdirectory(.\\glfw-3.4)

file(GLOB_RECURSE sources
  "${CMAKE_SOURCE_DIR}/src/*.c"
  "${CMAKE_SOURCE_DIR}/src/*.cpp"
  "${GLAD_GL}/src/*.c")
add_executable(learn_opengl ${sources})

target_link_libraries(learn_opengl glfw)
target_link_libraries(learn_opengl OpenGL::GL)
