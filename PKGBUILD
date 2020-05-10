# Script generated with import_catkin_packages.py.
# For more information: https://github.com/bchretien/arch-ros-stacks.
pkgdesc="ROS - rosbuild contains scripts for managing the CMake-based build system for ROS."
url='https://wiki.ros.org/rosbuild'

pkgname='ros-noetic-rosbuild'
pkgver='1.15.2'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(
	ros-noetic-catkin
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
	pkg-config
)

ros_depends=(
	ros-noetic-message-runtime
	ros-noetic-message-generation
	ros-noetic-catkin
)

depends=(
	${ros_depends[@]}
)

_dir="ros-${pkgver}/core/rosbuild"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros/ros/archive/${pkgver}.tar.gz")
sha256sums=('596bb5e04ece0ad0662d6d2ee9b4223aaa890770e83c7310ec71bf9c0c3c7b5e')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCMAKE_BUILD_TYPE=Release \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
		-DPYTHON_EXECUTABLE=/usr/bin/python3 \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
