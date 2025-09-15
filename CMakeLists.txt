cmake_minimum_required(VERSION 3.5)
add_definitions("-std=c++17")

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

# Define EMSDK_ROOT as the path to deps/emsdk relative to project root
set(EMSDK_ROOT "${CMAKE_SOURCE_DIR}/deps/emsdk")
# Add Emscripten include directory using EMSDK_ROOT
target_include_directories(${PROJECT_NAME} PRIVATE ${EMSDK_ROOT}/upstream/emscripten/cache/sysroot/include)

