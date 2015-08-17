# Maintainer: Gustavo Castro <gustawho[at]gmail[dot]com>

pkgname=telegram-qt5-git
pkgver=381.ccdd08c
pkgrel=2
pkgdesc="Qt5 bindings for the Telegram protocol"
arch=('i686' 'x86_64')
url="https://github.com/Kaffeine/telegram-qt/"
license=('GPL')
depends=('qt5-base')
makedepends=('cmake' 'git')
provides=('telegram-qt5')
conflicts=('telegram-qt5')
source=("git+https://github.com/Kaffeine/telegram-qt/")
md5sums=('SKIP')
options=('staticlibs')

pkgver() {
  cd telegram-qt
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../telegram-qt \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DCMAKE_BUILD_TYPE=Release \
    -DUSE_QT4=OFF
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
