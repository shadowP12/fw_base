cmake_minimum_required(VERSION 3.13)

set(CMAKE_CXX_STANDARD 14)

project(fw_project)

add_definitions(-DPROJECT_DIR="${CMAKE_CURRENT_SOURCE_DIR}")

file(GLOB_RECURSE SOURCE_FILES "src/*.h" "src/*.cpp")
add_executable(fw_project ${SOURCE_FILES})

# cgltf
add_library(cgltf INTERFACE)
target_include_directories(cgltf INTERFACE extern/cgltf)
target_link_libraries(fw_project PUBLIC cgltf)

# spark
add_subdirectory(extern/spark EXCLUDE_FROM_ALL spark.out)
target_link_libraries(fw_project PUBLIC spark)