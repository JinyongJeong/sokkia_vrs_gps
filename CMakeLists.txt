cmake_minimum_required(VERSION 2.8.3)
project(vrs_gps_driver)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  serial
  std_msgs
  message_generation

)

add_message_files(
  DIRECTORY msg
)

generate_messages(
   DEPENDENCIES
   std_msgs
)

catkin_package(
  CATKIN_DEPENDS
    serial    
    std_msgs
    message_runtime
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  include
)

add_definitions(-std=c++11)

add_executable(vrs_gps_driver src/vrs_gps_driver.cpp src/GeoCoordConv.cpp include/GeoCoordConv.h
src/basic_serial.cpp include/basic_serial.h)



target_link_libraries(vrs_gps_driver
  ${catkin_LIBRARIES}
)

#add_dependencies(vrs_gps_driver vrs_gps_driver_generate_messages_cpp)
add_dependencies(vrs_gps_driver ${catkin_EXPORTED_TARGETS})


