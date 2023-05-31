add_library(utils shader.cc shader.hpp)
target_link_libraries(utils PRIVATE glad::glad glm::glm)
