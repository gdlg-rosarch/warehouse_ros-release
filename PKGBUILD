# Script generated with Bloom
pkgdesc="ROS - Persistent storage of ROS messages"
url='http://ros.org/wiki/warehouse_ros'

pkgname='ros-lunar-warehouse-ros'
pkgver='0.9.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('gtest'
'ros-lunar-catkin'
'ros-lunar-geometry-msgs'
'ros-lunar-pluginlib'
'ros-lunar-roscpp'
'ros-lunar-rostest'
'ros-lunar-rostime'
'ros-lunar-std-msgs'
'ros-lunar-tf'
)

depends=('boost'
'ros-lunar-geometry-msgs'
'ros-lunar-pluginlib'
'ros-lunar-roscpp'
'ros-lunar-rostime'
'ros-lunar-std-msgs'
'ros-lunar-tf'
)

conflicts=()
replaces=()

_dir=warehouse_ros
source=()
md5sums=()

prepare() {
    cp -R $startdir/warehouse_ros $srcdir/warehouse_ros
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

