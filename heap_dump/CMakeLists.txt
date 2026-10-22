cmake_minimum_required(VERSION 3.20)
project(heap_dump VERSION 0.1.0 LANGUAGES C RC)

add_executable(heap_dump heap_dump.c heap_dump.rc)
target_link_libraries(heap_dump PRIVATE advapi32)

if (MSVC)
    target_compile_options(heap_dump PRIVATE /W4)
    set_property(TARGET heap_dump PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()
