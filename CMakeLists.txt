########################################################################
# Preamble
########################################################################

cmake_minimum_required( VERSION 3.14 )
project( catch-adapter LANGUAGES CXX )


########################################################################
# Project-wide setup
########################################################################

set( CMAKE_CXX_STANDARD 17 )
set( CMAKE_CXX_STANDARD_REQUIRED YES )

option( catch-adapter_unit_tests
    "Compile the catch-adapter unit tests and integrate with ctest" ON
    )
option( strict_compile
    "Treat all warnings as errors." ON
    )

# Compile flags
set( common_flags "-Wall" "-Wextra" "-Wpedantic" )
set( strict_flags "-Werror" )
set( release_flags "-O3" )
set( debug_flags "-O0" "-g" )


########################################################################
# Project targets
########################################################################

add_library( catch-adapter INTERFACE )
target_include_directories( catch-adapter
    INTERFACE src/single_include
    )
target_compile_options( catch-adapter INTERFACE
    ${common_flags}
    $<$<BOOL:${strict_compile}>:${strict_flags}>
    $<$<CONFIG:DEBUG>:${debug_flags}>
    $<$<CONFIG:RELEASE>:${release_flags}>
    )


#######################################################################
# Top-level Only
#######################################################################

if( CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR )

    # unit testing
    if( catch-adapter_unit_tests )
        include( cmake/unit_testing.cmake )
    endif()

endif()
