cmake_minimum_required(VERSION 3.18)

project(
  cpp_template # Change this
  VERSION 0.0.1
  LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

include(cmake/Cache.cmake)
include(cmake/Sanitizers.cmake)
include(cmake/Warnings.cmake)

file(
  GLOB_RECURSE
  ${PROJECT_NAME}_SRC 
  include/*.hpp include/*.h
  src/*.cpp src/*.hpp src/*.h
)

add_executable(${PROJECT_NAME} ${${PROJECT_NAME}_SRC})
target_include_directories(${PROJECT_NAME} PRIVATE include)

enable_sanitizers(${PROJECT_NAME})
set_project_warnings(${PROJECT_NAME})
