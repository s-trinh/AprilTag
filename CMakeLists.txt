project(AprilTag-crossplatform)

cmake_minimum_required ( VERSION 2.8 )

add_subdirectory(apriltag-2016-12-01)

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

# set the list of source files
set(test_cpp
  #${CMAKE_CURRENT_SOURCE_DIR}/example/apriltag_demo.c
  ${CMAKE_CURRENT_SOURCE_DIR}/example/opencv_demo.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/example/opencv_demo_offline.cc
)

# Copy test image
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/example/AprilTag.pgm ${CMAKE_CURRENT_BINARY_DIR} COPYONLY)

foreach(cpp ${test_cpp})
  get_filename_component(target ${cpp} NAME_WE)
  add_executable(${target} ${cpp})
  target_link_libraries(${target} APRILTAG_LIBRARY ${OpenCV_LIBS})
endforeach()
