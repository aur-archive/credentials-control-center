# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: Balló György <ballogyor+arch@gmail@com>

pkgname=credentials-control-center
pkgver=0.1.5
pkgrel=1
pkgdesc='Control panel for configuring online account credentials and settings'
arch=('i686' 'x86_64')
url='https://launchpad.net/gnome-control-center-signon'
license=('GPL3' 'LGPL3')
depends=('libaccounts-glib' 'libsignon-glib' 'gtk3')
makedepends=('gobject-introspection' 'vala' 'intltool' 'itstool')
install="${pkgname}.install"
source=("https://launchpad.net/gnome-control-center-signon/13.04/${pkgver}/+download/${pkgname}-${pkgver}.tar.xz")
sha256sums=('86424e646d60558c9174130b032df42ff6e0f82a8f57b8d93636322c889c6d78')

prepare() {
  cd ${pkgname}-${pkgver}

  sed -i 's/test/test -e/' online-accounts-preferences.in
}

build() {
  cd ${pkgname}-${pkgver}

  ./configure --prefix='/usr' --sysconfdir='/etc' --localstatedir='/var' --libexecdir="/usr/lib/${pkgname}" --disable-static
  make
}

package() {
  cd ${pkgname}-${pkgver}

  make DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
