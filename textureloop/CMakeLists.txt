add_executable(textureloop main.cc)
target_include_directories(textureloop PRIVATE ${Stb_INCLUDE_DIR})
target_link_libraries(textureloop PRIVATE glfw glad::glad utils)

add_custom_command(
  TARGET textureloop
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:textureloop>/textureloop_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/textureloop/shaders/"
    "$<TARGET_FILE_DIR:textureloop>/textureloop_dir")
