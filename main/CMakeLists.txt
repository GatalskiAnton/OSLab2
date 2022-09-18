cmake_minimum_required(VERSION 3.23)
project(main)

set(CMAKE_CXX_STANDARD 17)

add_executable(main main.cpp)

add_library(Number STATIC IMPORTED)
set_target_properties(Number PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/../Number/cmake-build-debug/libNumber.a)
set_target_properties(Number PROPERTIES INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/../Number)

add_library(Vector SHARED IMPORTED)
set_target_properties(Vector PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/../Vector/cmake-build-debug/libVector.so)
set_target_properties(Vector PROPERTIES INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/../Vector)

target_link_libraries(main Number)
target_link_libraries(main Vector)