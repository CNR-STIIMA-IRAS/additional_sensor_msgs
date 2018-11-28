cmake_minimum_required(VERSION 2.8.3)
project(additional_sensor_msgs)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  roscpp
  sensor_msgs
)

add_message_files(
  FILES
  JointInfo.msg
)

generate_messages(
  DEPENDENCIES
  sensor_msgs
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES additional_sensor_msgs
  CATKIN_DEPENDS  roscpp sensor_msgs
  DEPENDS 
)

include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
  PATTERN ".svn" EXCLUDE
)

## Mark other files for installation (e.g. launch and bag files, etc.)
install(FILES
  msg/JointInfo.msg
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

  
