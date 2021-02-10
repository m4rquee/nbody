cmake_minimum_required(VERSION 3.17)
project(nbody)

set(CMAKE_CXX_STANDARD 20)
set(THREADS_PREFER_PTHREAD_FLAG ON)

find_package(PkgConfig REQUIRED)
pkg_search_module(GLIB REQUIRED glib-2.0)

find_package(OpenGL REQUIRED)
find_package(Threads REQUIRED)
find_package(glfw3 3.3 REQUIRED)

file(GLOB_RECURSE SOURCE_FILES src/*.cpp)

include_directories(${GLIB_INCLUDE_DIRS})
include_directories(${GLFW_INCLUDE_DIRS})
include_directories(./include ./src)

add_executable(nbody main.cpp ${SOURCE_FILES})

target_link_libraries(nbody m Threads::Threads OpenGL::GL ${GLIB_LDFLAGS})
target_link_libraries(nbody glfw3 ${CMAKE_DL_LIBS})
