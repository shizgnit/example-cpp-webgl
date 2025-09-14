cmake_minimum_required(VERSION 3.1)
add_definitions("-std=c++14")

# Setup the project
set(PROJECT_NAME "example_cpp_webgl")
project(${PROJECT_NAME})
file(GLOB sources *.cpp)
add_executable(${PROJECT_NAME} ${sources})
set_target_properties(${PROJECT_NAME} PROPERTIES SUFFIX ".html")

# Find OpenGL
find_package(OpenGL REQUIRED)

# Link OpenGL to the executable
target_link_libraries(${PROJECT_NAME} ${OPENGL_gl_LIBRARY})

# Add OpenGL include directories
target_include_directories(${PROJECT_NAME} PRIVATE ${OPENGL_INCLUDE_DIR})

# Add Emscripten include directory
target_include_directories(${PROJECT_NAME} PRIVATE /Users/codeneko/Projects/emsdk/upstream/emscripten/cache/sysroot/include)

