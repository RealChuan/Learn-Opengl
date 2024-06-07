cmake_minimum_required(VERSION 3.25.1)

include(cmake/vcpkg.cmake)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
include(utils)

project(
  Learn-OpenGL
  VERSION 0.0.1
  DESCRIPTION "This project is used to learn OpenGL"
  HOMEPAGE_URL "https://github.com/RealChuan/Learn-OpenGL"
  LANGUAGES CXX)

include(cmake/common.cmake)

find_package(glad CONFIG REQUIRED)
if(glad_FOUND)
  message(STATUS "found glad")
endif()
find_package(glfw3 CONFIG REQUIRED)
if(glfw3_FOUND)
  message(STATUS "found glfw3")
endif()
find_package(glm CONFIG REQUIRED)
if(glm_FOUND)
  message(STATUS "found glm")
endif()
find_package(Stb REQUIRED)
if(Stb_FOUND)
  message(STATUS "found Stb")
endif()

add_subdirectory(hellowindow)
add_subdirectory(triangle)
add_subdirectory(rectangle)
add_subdirectory(utils)
add_subdirectory(shader)
add_subdirectory(texture)
add_subdirectory(textureloop)
add_subdirectory(texturemixed)
add_subdirectory(transform)
add_subdirectory(coordinate)
add_subdirectory(camera)
add_subdirectory(color)
add_subdirectory(light)
add_subdirectory(material)
