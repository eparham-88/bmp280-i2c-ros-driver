cmake_minimum_required(VERSION 2.8.3)
project(bar_bmp280)

add_compile_options(-std=c++14 -li2c)

find_package(catkin REQUIRED COMPONENTS roscpp sensor_msgs std_msgs genmsg)

## Declare ROS messages and services
#add_message_files(FILES Num.msg)

## Generate added messages and services
generate_messages(DEPENDENCIES std_msgs)

catkin_package(INCLUDE_DIRS include)

## Build talker and listener
include_directories(include ${catkin_INCLUDE_DIRS})
add_executable(bar_bmp280_node src/BMP280.cpp)
target_link_libraries(bar_bmp280_node ${catkin_LIBRARIES})
add_dependencies(bar_bmp280_node beginner_tutorials_generate_messages_cpp)

install(TARGETS bar_bmp280_node
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)