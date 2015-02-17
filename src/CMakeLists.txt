remake_ros_package(
  velodyne
  DEPENDS roscpp rospy rosbash sensor_msgs diagnostic_updater std_msgs
  EXTRA_BUILD_DEPENDS libvelodyne-dev libsnappy-dev
  EXTRA_RUN_DEPENDS libvelodyne libsnappy1
  DESCRIPTION "Driver for Velodyne HDL devices."
)
remake_ros_package_config_generate(PACKAGE velodyne EXTRA_CFLAGS -std=c++0x)
