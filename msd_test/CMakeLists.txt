cmake_minimum_required(VERSION 3.21)
project(msd_test VERSION 0.1.0 LANGUAGES CXX RC)

add_executable(msd_test msd_test.cpp msd_test.rc)
target_compile_features(msd_test PRIVATE cxx_std_17)
target_compile_definitions(msd_test PRIVATE UNICODE _UNICODE)
target_link_libraries(msd_test PRIVATE user32 advapi32)

if(MSVC)
    target_compile_options(msd_test PRIVATE /W4)
    set_property(TARGET msd_test PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()
