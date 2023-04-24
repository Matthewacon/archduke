cmake_minimum_required(VERSION 3.19)

#[[Ensure CMake generates a compilation command database]]
set(ENV{CMAKE_EXPORT_COMPILE_COMMANDS} ON)

project(
 archduke
 VERSION 1.0.0
 LANGUAGES CXX
 DESCRIPTION "0xCAFEBABE"
)

#[[Requied defaults]]
set(CMAKE_CXX_STANDARD 20)

#Explicitly disallow in-source builds
if("${PROJECT_SOURCE_DIR}" STREQUAL "${PROJECT_BINARY_DIR}")
 message(
  FATAL_ERROR
  "In-source builds are not permitted."
 )
endif()

#Collect sources
file(GLOB_RECURSE ARCH_DUKE_SOURCES "src/*.cpp" "src/**/*.cpp")

#Build executable
add_executable(archduke)
target_sources(archduke PUBLIC ${ARCH_DUKE_SOURCES})
target_include_directories(archduke PUBLIC include)
set_target_properties(archduke PROPERTIES LINKER_LANGUAGE CXX)
