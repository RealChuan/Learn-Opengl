add_executable(color main.cc)
target_link_libraries(color PRIVATE glfw glad::glad glm::glm utils)

add_custom_command(
  TARGET color
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:color>/color_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory "${PROJECT_SOURCE_DIR}/color/shaders/"
    "$<TARGET_FILE_DIR:color>/color_dir")
