cmake_minimum_required(VERSION 2.8.3)
project(gazebo_model_path_example)

find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
)

catkin_package(
  CATKIN_DEPENDS
  gazebo_ros
)

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(DIRECTORY models
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(DIRECTORY urdf
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(DIRECTORY worlds
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
