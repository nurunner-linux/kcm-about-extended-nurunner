pkgname=kcm-about-extended
pkgver=1.0
pkgrel=1
pkgdesc='Extended information to replace kio-sysinfo'
arch=('i686' 'x86_64')
url='https://github.com/ds9-extras/kcm-about-extended'
license=('LGPL')
depends=('kwin' 'networkmanager-qt')
makedepends=('git' 'extra-cmake-modules' 'kdoctools' 'python')
conflicts=('kdebase-workspace')
groups=('plasma')
source=('git://github.com/ds9-extras/kcm-about-extended'
        'nurunner-logo.svg'
        'kcm-about-extendedrc')
md5sums=('SKIP'
         '2f829374307a79271e18392f5ef01155'
         'b5ad5f1134e9eda4d2a1081991700489')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../${pkgname} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  make
}

pkgver() {
date +%Y.%m.%d
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install

# Install Nurunner logo
  install -Dm644 "$srcdir"/nurunner-logo.svg "$pkgdir"/usr/share/about-distro/nurunner-logo.svg
  install -Dm644 "$srcdir"/kcm-about-extendedrc "$pkgdir"/etc/xdg/kcm-about-extendedrc
}
