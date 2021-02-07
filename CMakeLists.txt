cmake_minimum_required(VERSION 3.2 FATAL_ERROR)
project(glTemplate)

find_package(OpenGL REQUIRED)

add_subdirectory(thirdparty/glad)
add_subdirectory(thirdparty/glfw)
add_subdirectory(thirdparty/glm)
add_subdirectory(thirdparty/soil2-cmake)
add_subdirectory(thirdparty/imgui-cmake)

set(LIBS opengl32 glad glfw glm soil2 imgui)

file(GLOB_RECURSE SOURCE_FILES 
	source/*.c
	source/*.cpp)

file(GLOB_RECURSE HEADER_FILES 
	source/*.h
    source/*.hpp)

add_executable(${PROJECT_NAME} ${HEADER_FILES} ${SOURCE_FILES})

target_compile_definitions(${PROJECT_NAME} PUBLIC IMGUI_IMPL_OPENGL_LOADER_GLAD)

target_link_libraries(${PROJECT_NAME} ${LIBS})