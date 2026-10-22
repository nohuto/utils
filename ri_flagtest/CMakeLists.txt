cmake_minimum_required(VERSION 3.20)
project(raw_input_flag_tests VERSION 0.1.0 LANGUAGES C RC)

add_executable(ri_0100 ri_mouse.c ri_0100.rc)
target_compile_definitions(ri_0100 PRIVATE WIN32_LEAN_AND_MEAN RI_FLAGS=0x0100 RI_NAME="ri_0100")

add_executable(ri_8100 ri_mouse.c ri_8100.rc)
target_compile_definitions(ri_8100 PRIVATE WIN32_LEAN_AND_MEAN RI_FLAGS=0x8100 RI_NAME="ri_8100")

if(MSVC)
    set_property(TARGET ri_0100 ri_8100 PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()
