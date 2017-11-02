cmake_minimum_required(VERSION 2.8.3)
project(generatepointcloud)
set(CMAKE_BUILD_TYPE "Debug")

find_package(catkin REQUIRED COMPONENTS
  pcl_ros
  rospy
  sensor_msgs
  std_msgs
  tf2
  image_geometry
  image_transport
  cv_bridge
)

# 增加PCL库的依赖
FIND_PACKAGE( PCL REQUIRED COMPONENTS common io )

# 增加opencv的依赖
FIND_PACKAGE( OpenCV REQUIRED )
#增加pcl的依赖
FIND_PACKAGE(PCL 1.7 REQUIRED)
# 添加头文件和库文件
ADD_DEFINITIONS( ${PCL_DEFINITIONS} )
INCLUDE_DIRECTORIES( ${PCL_INCLUDE_DIRS}  )
LINK_LIBRARIES( ${PCL_LIBRARY_DIRS} )

ADD_EXECUTABLE( point_cloud src/point_cloud.cpp )
TARGET_LINK_LIBRARIES( point_cloud ${OpenCV_LIBS}
    ${PCL_LIBRARIES} )
