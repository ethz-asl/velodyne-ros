cmake_minimum_required(VERSION 2.4.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
set(ROS_BUILD_TYPE Release)

rosbuild_init()

set(CMAKE_CXX_FLAGS "-std=c++0x")

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

rosbuild_genmsg()

# libvelodyne
find_path(LIBVELODYNE_INCLUDE_DIR sensor/AcquisitionThread.h
  /usr/include
  PATH_SUFFIXES
  libvelodyne
)

message(Found ${LIBVELODYNE_INCLUDE_DIR})

find_library(LIBVELODYNE_SENSOR_LIBRARY velodyne-sensor
  /usr/lib
)
find_library(LIBVELODYNE_COM_LIBRARY velodyne-com
  /usr/lib
)
find_library(LIBVELODYNE_BASE_LIBRARY velodyne-base
  /usr/lib
)
find_library(LIBVELODYNE_EXCEPTIONS_LIBRARY velodyne-exceptions
  /usr/lib
)
find_library(LIBVELODYNE_DATA_STRUCTURES_LIBRARY velodyne-data-structures
  /usr/lib
)

include_directories(
  ${LIBVELODYNE_INCLUDE_DIR}
)

rosbuild_add_executable(velodyne_hdl_64ES2 src/velodyne_hdl_64ES2.cpp)
target_link_libraries(velodyne_hdl_64ES2
  ${LIBVELODYNE_SENSOR_LIBRARY} ${LIBVELODYNE_COM_LIBRARY}
  ${LIBVELODYNE_BASE_LIBRARY} ${LIBVELODYNE_EXCEPTIONS_LIBRARY}
  ${LIBVELODYNE_DATA_STRUCTURES_LIBRARY}
)

rosbuild_add_executable(imu_velodyne_hdl_32E src/imu_velodyne_hdl_32E.cpp)
target_link_libraries(imu_velodyne_hdl_32E
  ${LIBVELODYNE_SENSOR_LIBRARY} ${LIBVELODYNE_COM_LIBRARY}
  ${LIBVELODYNE_BASE_LIBRARY} ${LIBVELODYNE_EXCEPTIONS_LIBRARY}
  ${LIBVELODYNE_DATA_STRUCTURES_LIBRARY}
)