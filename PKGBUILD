# Maintainer: Antonio Rojas <arojas@archlinux.org>

pkgname=gammaray
pkgver=git
pkgrel=1
pkgdesc='A tool for examining the internals of a Qt application and to some extent also manipulate it'
arch=(x86_64)
url='https://www.kdab.com/gammaray/'
license=(GPL)
depends=(syntax-highlighting qt6-tools qt6-svg qt6-3d)
makedepends=(cmake kcoreaddons qt5-script qt5-wayland qt5-webengine qt5-scxml qt5-location qt5-connectivity doxygen glslang)
optdepends=('qt6-wayland: Wayland compositor inspector plugin'
            'qt6-webengine: web inspector plugin'
            'qt6-scxml: state machine viewer plugin'
            'qt6-connectivity: bluetooth plugin'
            'qt6-script: script engine debugger plugin'
            'kcoreaddons: KJob tracker plugin')
source=('https://github.com/KDAB/GammaRay/archive/refs/heads/master.zip')
sha256sums=('SKIP')
validpgpkeys=('SKIP')

prepare() {
# Fix plugin install dir
  sed -e 's|plugins/gammaray|lib/qt/plugins/gammaray|' -i GammaRay-master/CMakeLists.txt
}

build() {
  cmake -B build -S GammaRay-master \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DGAMMARAY_INSTALL_QT_LAYOUT=ON \
    -DECM_MKSPECS_INSTALL_DIR=/usr/lib/qt/mkspecs/modules \
    -DPLUGIN_INSTALL_DIR=/usr/lib/qt/plugins/gammaray
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
