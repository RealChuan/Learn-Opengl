add_executable(light main.cc)
target_link_libraries(light PRIVATE glfw glad::glad glm::glm utils)

add_custom_command(
  TARGET light
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:light>/light_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory "${PROJECT_SOURCE_DIR}/light/shaders/"
    "$<TARGET_FILE_DIR:light>/light_dir")
