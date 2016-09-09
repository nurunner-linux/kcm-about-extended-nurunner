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
        'nurunner-logo-grey.png'
        'kcm-about-extendedrc')
md5sums=('SKIP'
         'cd6c97760883ccf780e0bbdd926fbb01'
         '87acbf6fcef86f1b63bced51ac436935')

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
  install -Dm644 "$srcdir"/nurunner-logo-grey.png "$pkgdir"/usr/share/about-distro/nurunner-logo-grey.png
  install -Dm644 "$srcdir"/kcm-about-extendedrc "$pkgdir"/etc/xdg/kcm-about-extendedrc
}
