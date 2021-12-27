#
# \file       CMakeLists.txt
# \author     GrandChris
# \date       2021-06-20
# \brief      Base project file
#

cmake_minimum_required(VERSION 3.20)

# Create the project
project("constexpr_sml" CXX)

# Export compile commands for VSCode C++ Intellisense
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_compile_options(
    -fdiagnostics-color
    -Wall 
)

# include_directories(${CMAKE_SOURCE_DIR}/vcpkg_installed/x64-mingw-static/include)
# link_directories(${CMAKE_SOURCE_DIR}/vcpkg_installed/x64-mingw-static/lib)
# link_directories(${CMAKE_SOURCE_DIR}/vcpkg_installed/x64-mingw-static/lib/manual-link)

# add library
add_executable(${PROJECT_NAME})

# include directories
target_include_directories(${PROJECT_NAME} PUBLIC
    "${CMAKE_SOURCE_DIR}/source"
    # "${CMAKE_SOURCE_DIR}/app"
)

# add source files
file(GLOB SOURCE_FILES CONFIGURE_DEPENDS
    "${CMAKE_SOURCE_DIR}/source/sml/*.cpp"
    # "${CMAKE_SOURCE_DIR}/source/*/*.cpp"
)

target_sources(${PROJECT_NAME} PRIVATE ${SOURCE_FILES})

# target_link_libraries(${PROJECT_NAME} PRIVATE 
#     glm
# )


# add_subdirectory(app)
# add_subdirectory(VulkanErruption)