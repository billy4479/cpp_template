cmake_minimum_required(VERSION 3.10)

project(cpp_template)

file( GLOB SOURCES src/*.cpp )

add_executable( cpp_template ${SOURCES} )