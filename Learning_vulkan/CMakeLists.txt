# CMakeList.txt : CMake project for Learning_vulkan, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

# Add source to this project's executable.
add_executable (Learning_vulkan "Learning_vulkan.cpp" )

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

find_package(Vulkan REQUIRED)

add_subdirectory(external/glfw)
add_subdirectory(external/glm)

target_link_libraries(Learning_vulkan 
	PRIVATE glfw
	PRIVATE ${Vulkan_LIBRARIES}
	PRIVATE glm
)
include_directories(Learning_vulkan PRIVATE ${Vulkan_INCLUDE_DIRS})

# TODO: Add tests and install targets if needed.
