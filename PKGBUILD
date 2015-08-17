# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - A multiplexer for command velocity inputs."
url='http://ros.org/wiki/yocs_cmd_vel_mux'

pkgname='ros-hydro-yocs-cmd-vel-mux'
pkgver='0.5.3'
_pkgver_patch=1
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-nodelet
  ros-hydro-roscpp
  ros-hydro-geometry-msgs
  ros-hydro-catkin
  ros-hydro-dynamic-reconfigure
  ros-hydro-pluginlib)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  yaml-cpp)

ros_depends=(ros-hydro-roscpp
  ros-hydro-geometry-msgs
  ros-hydro-nodelet
  ros-hydro-dynamic-reconfigure
  ros-hydro-pluginlib)
depends=(${ros_depends[@]}
  yaml-cpp)

_tag=release/hydro/yocs_cmd_vel_mux/${pkgver}-${_pkgver_patch}
_dir=yocs_cmd_vel_mux
source=("${_dir}"::"git+https://github.com/yujinrobot-release/yujin_ocs-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
