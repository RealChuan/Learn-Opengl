add_executable(texturemixed main.cc)
target_include_directories(texturemixed PRIVATE ${Stb_INCLUDE_DIR})
target_link_libraries(texturemixed PRIVATE glfw glad::glad utils)

add_custom_command(
  TARGET texturemixed
  POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E make_directory
          "$<TARGET_FILE_DIR:texture>/texturemixed_dir/"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/texturemixed/shaders/"
    "$<TARGET_FILE_DIR:texturemixed>/texturemixed_dir"
  COMMAND
    ${CMAKE_COMMAND} -E copy_directory
    "${PROJECT_SOURCE_DIR}/texturemixed/images/"
    "$<TARGET_FILE_DIR:texturemixed>/texturemixed_dir")
