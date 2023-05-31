add_library(utils camera.cc camera.hpp shader.cc shader.hpp)
target_link_libraries(utils PRIVATE glad::glad glm::glm)
