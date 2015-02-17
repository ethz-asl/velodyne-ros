remake_find_package(libvelodyne CONFIG)
remake_find_library(snappy snappy.h)

remake_include(${LIBVELODYNE_INCLUDE_DIRS})
remake_include(${SNAPPY_HEADERS})

remake_ros_package_add_library(velodyne-ros LINK ${LIBVELODYNE_LIBRARIES}
  ${SNAPPY_LIBRARY})
