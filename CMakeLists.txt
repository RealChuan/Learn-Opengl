cmake_minimum_required(VERSION 3.16)

if(CMAKE_HOST_WIN32)
  set(CMAKE_TOOLCHAIN_FILE
      "C:/vcpkg/scripts/buildsystems/vcpkg.cmake"
      CACHE STRING "Vcpkg toolchain file")
elseif(CMAKE_HOST_APPLE)
  set(CMAKE_TOOLCHAIN_FILE
      "/usr/local/share/vcpkg/scripts/buildsystems/vcpkg.cmake"
      CACHE STRING "Vcpkg toolchain file")
elseif(CMAKE_HOST_UNIX)
  set(CMAKE_TOOLCHAIN_FILE
      "/usr/local/share/vcpkg/scripts/buildsystems/vcpkg.cmake"
      CACHE STRING "Vcpkg toolchain file")
endif()

project(
  opengl-learn
  VERSION 0.1
  LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_CURRENT_SOURCE_DIR ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_DEBUG_POSTFIX d)

if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message("Setting build type to 'RelWithDebInfo' as none was specified.")
  set(CMAKE_BUILD_TYPE
      RelWithDebInfo
      CACHE STRING "Choose the type of build." FORCE)
  # Set the possible values of build type for cmake-gui
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release"
                                               "MinSizeRel" "RelWithDebInfo")
endif()

if(CMAKE_SIZEOF_VOID_P EQUAL 8)
  set(CURRENT_PLATFORM "-64")
else()
  set(CURRENT_PLATFORM "-32")
endif()

message(STATUS "Current Platform is ${CURRENT_PLATFORM}")

# 设定可执行二进制文件的目录
set(EXECUTABLE_OUTPUT_PATH
    ${PROJECT_SOURCE_DIR}/bin${CURRENT_PLATFORM}/${CMAKE_BUILD_TYPE}) # 源文件目录
# SET(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)     #输出文件目录

# 设定存放编译出来的库文件的目录
set(LIBRARY_OUTPUT_PATH
    ${PROJECT_SOURCE_DIR}/bin${CURRENT_PLATFORM}/${CMAKE_BUILD_TYPE})
# SET(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/lib)

# 并且把该目录设为连接目录
link_directories(
  ${PROJECT_SOURCE_DIR}/bin${CURRENT_PLATFORM}/${CMAKE_BUILD_TYPE})
# LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/lib)

include_directories(${PROJECT_SOURCE_DIR})

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
