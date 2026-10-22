cmake_minimum_required(VERSION 3.20)

project(GameModeTools VERSION 0.1.0 LANGUAGES C RC)

add_executable(gm_effects gm_effects.c gm_effects.rc)
target_compile_definitions(gm_effects PRIVATE UNICODE _UNICODE WIN32_LEAN_AND_MEAN)
target_compile_options(gm_effects PRIVATE $<$<C_COMPILER_ID:MSVC>:/W4>)
target_link_libraries(gm_effects PRIVATE user32)

if(MSVC)
    set_property(TARGET gm_effects PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()
