# Maintainer: Yoann Laissus <yoann dot laissus at gmail dot com"
# Contributor Kuba Serafinowski <zizzfizzix(at)gmail(dot)com>
# https://github.com/zizzfizzix/pkgbuilds

##############################################################
#### The section below can be adjusted to suit your needs ####
##############################################################

# What type of build do you want?
# See http://techbase.kde.org/Development/CMake/Addons_for_KDE#Buildtypes to check what is supported.
# Default is RelWithDebInfo to help with debugging.

_buildtype="Release"

##############################################################
_name=ocsync
pkgname=ocsync-beta
pkgver=0.91.1
pkgrel=1
pkgdesc="A file synchronizer especially designed for you, the normal user. Dependency of owncloud-client. Beta version."
arch=("i686" "x86_64")
url="http://www.csync.org"
license=('GPL2')
depends=('sqlite3' 'iniparser' 'neon')
makedepends=('cmake')
optdepends=('libssh: sftp support')
provides=('csync' 'csync-owncloud' 'ocsync')
conflicts=('csync' 'csync-owncloud' 'ocsync')
backup=('etc/ocsync/ocsync.conf' 'etc/ocsync/ocsync_exclude.conf')
source=("http://download.owncloud.com/download/testing/${_name}-${pkgver}.tar.bz2")
md5sums=('688d0b8863384ef735461e6c2fd04107')

options=('staticlibs' '!strip')

prepare() {
  if [[ -e ${srcdir}/${_name}-${pkgver}-build ]]; then rm -rf ${srcdir}/${_name}-${pkgver}-build; fi
  mkdir ${srcdir}/${_name}-${pkgver}-build
}

build() {
  cd ${srcdir}/${_name}-${pkgver}-build
  
  cmake -DCMAKE_BUILD_TYPE=${_buildtype} \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DSYSCONF_INSTALL_DIR=/etc \
        ../${_name}-${pkgver}
  make
}
package() {
  cd ${srcdir}/${_name}-${pkgver}-build
  make DESTDIR=${pkgdir} install
}
