# Script generated with Bloom
pkgdesc="ROS - This is a ROS 3rd-party wrapper <a href="http://www.ros.org/reps/rep-0136.html">(see REP-136 for more detail)</a> of Andrea Censi's CSM package. From <a href="http://censi.mit.edu/software/csm/">the official website</a>: <ul> The C(anonical) Scan Matcher (CSM) is a pure C implementation of a very fast variation of ICP using a point-to-line metric optimized for range-finder scan matching. It is robust enough to be used in industrial prototypes of autonomous mobile robotics, for example at Kuka. CSM is used by a variety of people, though it is hard to keep track because of the open source distribution, especially as packaged in ROS. If you use this software for something cool, let me know. </ul>"
url='http://censi.mit.edu/software/csm'

pkgname='ros-kinetic-csm'
pkgver='1.0.2_2'
pkgrel=1
arch=('any')
license=('LGPL'
)

makedepends=('cmake'
'gsl'
)

depends=('gsl'
'ros-kinetic-catkin'
)

conflicts=()
replaces=()

_dir=csm
source=()
md5sums=()

prepare() {
    cp -R $startdir/csm $srcdir/csm
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
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

