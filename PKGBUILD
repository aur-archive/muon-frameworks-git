# Maintainer: Antonio Rojas 

pkgname=muon-frameworks-git
pkgver=r3257.547f8df
pkgrel=1
pkgdesc='A collection of package management tools for KDE'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/extragear/sysadmin/muon'
license=('LGPL')
depends=('packagekit-qt5' 'kdeclarative')
makedepends=('extra-cmake-modules' 'git' 'python')
conflicts=('muon')
provides=('muon')
source=('git://anongit.kde.org/muon.git#branch=frameworks')
md5sums=('SKIP')

pkgver() {
  cd muon
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../muon \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DQML_INSTALL_DIR=lib/qt/qml
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
