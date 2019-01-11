cmake_minimum_required(VERSION 3.11)

project(DualContour)
set(CMAKE_CXX_STANDARD 11)
find_package(SDL2 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)

add_executable(dual-contouring
	DualContouringSample/density.cpp
	DualContouringSample/density.h
	DualContouringSample/glsl_program.cpp
	DualContouringSample/glsl_program.h
	DualContouringSample/main.cpp
	DualContouringSample/mesh.cpp
	DualContouringSample/mesh.h
	DualContouringSample/octree.cpp
	DualContouringSample/octree.h
	DualContouringSample/qef.cpp
	DualContouringSample/qef.h
	DualContouringSample/svd.cpp
	DualContouringSample/svd.h
)

target_include_directories(dual-contouring PRIVATE DualContouringSample)
target_link_libraries(dual-contouring SDL2 ${OPENGL_LIBRARIES} ${GLEW_LIBRARIES})
configure_file(DualContouringSample/shader.frag ${CMAKE_BINARY_DIR} COPYONLY)
configure_file(DualContouringSample/shader.vert ${CMAKE_BINARY_DIR} COPYONLY)
