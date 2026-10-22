cmake_minimum_required(VERSION 3.20)
project(riflags VERSION 0.1.0 LANGUAGES C RC)

add_executable(riflags riflags.c riflags.rc)
target_compile_definitions(riflags PRIVATE WIN32_LEAN_AND_MEAN)

add_library(riprobe SHARED riprobe.c riprobe.rc)
target_compile_definitions(riprobe PRIVATE WIN32_LEAN_AND_MEAN)

if(MSVC)
    set_property(TARGET riflags riprobe PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()
