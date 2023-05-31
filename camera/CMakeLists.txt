add_executable(camera main.cc)
target_include_directories(camera PRIVATE ${Stb_INCLUDE_DIR})
target_link_libraries(camera PRIVATE glfw glad::glad glm::glm utils)

add_custom_command(
  TARGET camera
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:camera>/camera_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory "${PROJECT_SOURCE_DIR}/camera/shaders/"
    "$<TARGET_FILE_DIR:camera>/camera_dir"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory "${PROJECT_SOURCE_DIR}/camera/images/"
    "$<TARGET_FILE_DIR:camera>/camera_dir")
