cmake_minimum_required(VERSION 3.20)

project(mmcss_task VERSION 0.1.0 LANGUAGES C RC)

add_executable(mmcss_task mmcss_task.c mmcss_task.rc)
target_link_libraries(mmcss_task PRIVATE avrt)

if(MSVC)
    set_property(TARGET mmcss_task PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()
