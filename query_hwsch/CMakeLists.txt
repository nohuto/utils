cmake_minimum_required(VERSION 3.20)
project(query_hwsch VERSION 0.1.0 LANGUAGES C RC)

add_executable(query_hwsch query_hwsch.c query_hwsch.rc)

if (MSVC)
  target_compile_options(query_hwsch PRIVATE /W4)
  set_property(TARGET query_hwsch PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
else()
  target_compile_options(query_hwsch PRIVATE -Wall -Wextra)
endif()
