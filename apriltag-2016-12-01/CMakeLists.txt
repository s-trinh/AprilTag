project(APRILTAG_LIBRARY)

include_directories(common)

file(GLOB lib_srcs *.c common/*.c)
file(GLOB lib_hdrs *.h common/*.h)

find_package (Threads REQUIRED)

add_library(APRILTAG_LIBRARY ${lib_srcs} ${lib_hdrs})
target_link_libraries( APRILTAG_LIBRARY ${CMAKE_THREAD_LIBS_INIT} )

target_include_directories (APRILTAG_LIBRARY PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
