cmake_minimum_required(VERSION 3.18)

project(cpp_template)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_program(CCACHE_FOUND ccache)
if(CCACHE_FOUND)
    message(STATUS "Found ccache")
    set(CMAKE_CXX_COMPILER_LAUNCHER ccache)
endif()

aux_source_directory(src ${PROJECT_NAME}_SRC)

add_executable(${PROJECT_NAME} ${${PROJECT_NAME}_SRC})

target_compile_options(${PROJECT_NAME} PRIVATE
  $<$<CXX_COMPILER_ID:MSVC>:/W4 /WX>
  $<$<NOT:$<CXX_COMPILER_ID:MSVC>>: -Wall -Wextra -pedantic -Werror>
)

