cmake_minimum_required(VERSION 3.0.2)
project(ros_tutorials_topic)

### Find catkin and any catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp std_msgs message_generation)

## Declare ROS messages and services
add_message_files(FILES MsgTutorial.msg)

## Generate added messages and services
generate_messages(DEPENDENCIES std_msgs)

## Declare a catkin package
catkin_package(
  #INCLUDE_DIRS include
  LIBRARIES ros_tutorials_topic
  CATKIN_DEPENDS roscpp std_msgs
  DEPENDS system_lib
)

## Build node
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(topic_publisher src/topic_publisher.cpp)
target_link_libraries(topic_publisher ${catkin_LIBRARIES})
add_dependencies(topic_publisher ros_tutorials_topic_generate_messages_cpp)

add_executable(topic_subscriber src/topic_subscriber.cpp)
target_link_libraries(topic_subscriber ${catkin_LIBRARIES})
add_dependencies(topic_subscriber ros_tutorials_topic_generate_messages_cpp)