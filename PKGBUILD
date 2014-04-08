# Maintainer: carstene1ns <url/mail: arch carsten-teibes de>
# Contributor: Gerardo Marset <gammer1994@gmail.com>
# Contributor: Aaron Lindsay <aerial9@gmail.com>
# Contributor: Vithon <ratm@archlinux.us>
# Contributor: Alain

pkgname=libfat-nds
pkgver=1.0.12
pkgrel=1
pkgdesc="Library for accessing FAT filesystems from Nintendo DS homebrew"
license=('custom')
arch=('any')
url="http://chishm.drunkencoders.com/libfat/"
depends=('libnds')
source=("http://downloads.sourceforge.net/sourceforge/devkitpro/libfat-src-$pkgver.tar.bz2")
sha256sums=('b36c26766f0fe13cd1ef822242dd2de09ba4598cbd1d7ddbb48cdaeea7e621af')
options=(!strip staticlibs)

build() {
  source /etc/profile.d/devkitarm.sh
  make nds-release
}

package() {
  export DEVKITPRO="$pkgdir"/opt/devkitpro

  install -d "$DEVKITPRO"/libnds/{lib,include}
  make nds-install
  # license
  install -d "$pkgdir"/usr/share/licenses/$pkgname
  head -n 30 include/fat.h > "$pkgdir"/usr/share/licenses/$pkgname/license.txt
}
