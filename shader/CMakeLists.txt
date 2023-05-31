add_executable(shader main.cc)
target_link_libraries(shader PRIVATE glfw glad::glad utils)

add_custom_command(
  TARGET shader
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:shader>/shader_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory "${PROJECT_SOURCE_DIR}/shader/shaders/"
    "$<TARGET_FILE_DIR:shader>/shader_dir")
