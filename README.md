# velodyne-ros

## Synopsis

ROS driver for Velodyne HDL devices.

**Author(s):** Jerome Maye, Ralf Kaestner

**Maintainer:** Ralf Kaestner <ralf.kaestner@gmail.com>

**License:** GNU Lesser General Public License (LGPL)

**Operating system(s):** Debian-based Linux

**Package PPA:** ppa:ethz-asl/ros

## Description

This project provides a ROS driver for Velodyne HDL devices. It builds on
[libvelodyne](http://github.com/ethz-asl/libvelodyne) and currently supports
the following sensor types:

* Velodyne HDL-64E
* Velodyne HDL-32E

## Installation

Here, we assume you intend to build/install the project for the ROS
distribution named `ROS_DISTRO`.

### Installing from packages (recommended for Ubuntu LTS users)

The maintainers of this project provide binary packages for the latest Ubuntu
LTS releases and commonly used system architectures. To install these packages,
you may follow these instructions:

* Add the drivers PPA to your APT sources by issuing 

  ```
  sudo add-apt-repository ppa:ethz-asl/drivers
  ```

  on the command line

* To re-synchronize your package index files, run

  ```
  sudo apt-get update
  ```

* Install all project packages and their dependencies through

  ```
  sudo apt-get install ros-ROS_DISTRO-velodyne
  ```

  or using your favorite package management tool

### Building from source

This project may be built using the CMake build system with an open-source
macro extension called ReMake.

#### Installing build dependencies

The build dependencies of this project are available from the standard
package repositories of recent Ubuntu and ROS releases. To install them,
simply use the command

```
sudo apt-get install libsnappy-dev ros-ROS_DISTRO-roscpp, ros-ROS_DISTRO-rospy, ros-ROS_DISTRO-rosbash, ros-ROS_DISTRO-message-generation, ros-ROS_DISTRO-std-msgs, ros-ROS_DISTRO-sensor-msgs, ros-ROS_DISTRO-diagnostic-updater

```
The Velodyne driver library (and its dependencies) may conveniently be
installed from the package PPAs of the project maintainers. To install them,
you may follow these instructions:

* Add the drivers PPA to your APT sources by issuing 

  ```
  sudo add-apt-repository ppa:ethz-asl/drivers
  ```

  on the command line

* To re-synchronize your package index files, run

  ```
  sudo apt-get update
  ```

* Install the required dependencies through

  ```
  sudo apt-get install libvelodyne-dev
  ```

  or using your favorite package management tool

#### Building with ReMake

##### Preparing the build system

If you already have installed ReMake on your build system, you may
skip this step. Otherwise, before attempting to build this project the
traditional CMake way, you must install ReMake following
[these instructions](https://github.com/kralf/remake).

##### Building with CMake

Once ReMake is available on your build system, you may attempt to build this
project the CMake way. Assuming that you have cloned the project sources into
`PROJECT_DIR`, a typical out-of-source build might look like this:

* Create a build directory using 

  ```
  mkdir -p PROJECT_DIR/build
  ```

* Switch into the build directoy by 

  ```
  cd PROJECT_DIR/build
  ```

* In the build directory, run 

  ```
  cmake -DROS_DISTRIBUTION=ROS_DISTRO PROJECT_DIR
  ```

  to configure the build

* If you want to inspect or modify the build configuration, issue 

  ```
  ccmake PROJECT_DIR
  ```

* Build the project using 

  ```
  make
  ```

* If you intend to install the project, call 

  ```
  make packages_install
  ```

  (from packages on Debian-based Linux only) or 

  ```
  make install
  ```

## API documentation

This project does not yet provide any API documentation.

## Feature requests and bug reports

If you would like to propose a feature for this project, please consider
contributing or send a feature request to the project authors. Bugs may be
reported through the project's issue page.

## Further reading

For additional information of the Robot Operating System (ROS), please refer
to the official [ROS documentation](http://wiki.ros.org).
