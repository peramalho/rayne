cmake_minimum_required(VERSION 3.16)
project(app)

# set the output directory for built objects.
# This makes sure that the dynamic library goes into the build directory automatically.
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")

# This assumes the SDL source is available in vendored/SDL
add_subdirectory(vendored/SDL EXCLUDE_FROM_ALL)

# Create your game executable target as usual
add_executable(rayne src/main.cpp src/game_manager.cpp)

# Link to the actual SDL3 library.
target_link_libraries(rayne PRIVATE SDL3::SDL3)