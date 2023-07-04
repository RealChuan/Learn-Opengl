add_executable(material main.cc)
target_link_libraries(material PRIVATE glfw glad::glad glm::glm utils)

add_custom_command(
  TARGET material
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:material>/material_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/material/shaders/"
    "$<TARGET_FILE_DIR:material>/material_dir")
