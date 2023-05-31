add_executable(transform main.cc)
target_include_directories(transform PRIVATE ${Stb_INCLUDE_DIR})
target_link_libraries(transform PRIVATE glfw glad::glad glm::glm utils)

add_custom_command(
  TARGET transform
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:transform>/transform_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/transform/shaders/"
    "$<TARGET_FILE_DIR:transform>/transform_dir"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/transform/images/"
    "$<TARGET_FILE_DIR:transform>/transform_dir")
