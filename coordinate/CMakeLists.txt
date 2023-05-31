add_executable(coordinate main.cc)
target_include_directories(coordinate PRIVATE ${Stb_INCLUDE_DIR})
target_link_libraries(coordinate PRIVATE glfw glad::glad glm::glm utils)

add_custom_command(
  TARGET coordinate
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:coordinate>/coordinate_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/coordinate/shaders/"
    "$<TARGET_FILE_DIR:coordinate>/coordinate_dir"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/coordinate/images/"
    "$<TARGET_FILE_DIR:coordinate>/coordinate_dir")
