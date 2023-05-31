add_executable(texture main.cc)
target_include_directories(texture PRIVATE ${Stb_INCLUDE_DIR})
target_link_libraries(texture PRIVATE glfw glad::glad utils)

add_custom_command(
  TARGET texture
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:texture>/texture_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory "${PROJECT_SOURCE_DIR}/texture/shaders/"
    "$<TARGET_FILE_DIR:texture>/texture_dir"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory "${PROJECT_SOURCE_DIR}/texture/images/"
    "$<TARGET_FILE_DIR:texture>/texture_dir")
