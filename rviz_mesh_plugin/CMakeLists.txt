cmake_minimum_required(VERSION 3.5)
project(rviz_mesh_plugin)

set(CMAKE_CXX_STANDARD 14)

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rviz_common REQUIRED)
find_package(rviz_rendering REQUIRED)
find_package(std_msgs REQUIRED)
find_package(mesh_msgs REQUIRED)
find_package(pluginlib REQUIRED)

## This setting causes Qt's "MOC" generation to happen automatically.
set(CMAKE_AUTOMOC ON)

find_package(Qt5 COMPONENTS Core Gui OpenGL Widgets REQUIRED)

add_definitions(-DQT_NO_KEYWORDS)


set(SOURCE_FILES
  src/trianglemesh_display.cpp
  src/trianglemesh_visual.cpp
  src/textured_mesh_display.cpp
  src/textured_mesh_visual.cpp
  src/face_selection_tool.cpp
  src/mesh_pose_tool.cpp
  src/mesh_goal_tool.cpp
)

add_library(rviz_mesh_plugin ${SOURCE_FILES})
ament_target_dependencies(rviz_mesh_plugin PUBLIC
  mesh_msgs
  pluginlib
  rclcpp
  rviz_common
  rviz_rendering
  OGRE
  std_msgs
)
message("rviz_rendering_INCLUDE_DIRS: ${rviz_rendering_INCLUDE_DIRS}")
message("OGRE_INCLUDE_DIRS: ${OGRE_INCLUDE_DIRS}")
message("Qt_INCLUDE_DIRS: ${Qt_INCLUDE_DIRS}")
message("QT_INCLUDE_DIRS: ${QT_INCLUDE_DIRS}")
message("Qt5_INCLUDE_DIRS: ${Qt5_INCLUDE_DIRS}")
message("QT5_INCLUDE_DIRS: ${QT5_INCLUDE_DIRS}")
target_include_directories(rviz_mesh_plugin PUBLIC
  ${rviz_rendering_INCLUDE_DIRS}
  ${rviz2_INCLUDE_DIRS}
  ${mesh_msgs_INCLUDE_DIRS}
  ${OGRE_INCLUDE_DIRS}
)
target_link_libraries(rviz_mesh_plugin PUBLIC
  Qt5::Core Qt5::Widgets Qt5::OpenGL Qt5::Gui)


ament_export_dependencies(
  Qt5
  mesh_msgs
  rclcpp
  rviz_common
  rviz_rendering
  OGRE
  std_msgs
)

#
#install(TARGETS rviz_mesh_plugin
#  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
#)
#install(FILES
#  rviz_plugin.xml
#  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
#
#install(DIRECTORY icons/
#  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/icons)

ament_package()
