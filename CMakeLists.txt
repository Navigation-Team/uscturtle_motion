cmake_minimum_required(VERSION 2.8.3)
project(uscturtle_motion)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  geometry_msgs
  message_generation
  ros_esccontrol
)

add_service_files(FILES GoStraight.srv)
generate_messages(DEPENDENCIES std_msgs)

## System dependencies are found with CMake's conventions
# find_package(Boost REQUIRED COMPONENTS system)


###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES ros_esccontrol
  CATKIN_DEPENDS roscpp std_msgs
#  DEPENDS system_lib
)

###########
## Build ##
###########

set(CMAKE_CXX_STANDARD 11)

## Specify additional locations of header files
## Your package locations should be listed before other locations
# include_directories(include)
include_directories(
   ${catkin_INCLUDE_DIRS}
)

add_executable(uscturtle_motion src/turtle_motion.cpp)
target_link_libraries(uscturtle_motion ${catkin_LIBRARIES})

add_executable(uscturtle_motor_test src/turtle_motor_test.cpp)
target_link_libraries(uscturtle_motor_test ${catkin_LIBRARIES})

