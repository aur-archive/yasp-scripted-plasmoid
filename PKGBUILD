# Maintainer: t3ddy  <t3ddy1988 "at" gmail {dot} com>
# Contributor: Raphael Weber <r_weber@gmx.net>

pkgname=yasp-scripted-plasmoid
pkgver=1.0.8a
pkgrel=1
pkgdesc="Yet Another System Monitor - but more configurable"
arch=('i686' 'x86_64')
url="http://www.kde-look.org/content/show.php/Yasp-Scripted+%28Systemmonitor%29?content=109367"
license=('GPL')
depends=('kdebase-workspace>=4.2')
makedepends=('gcc' 'cmake' 'automoc4')
install=yasp-scripted-plasmoid.install
source=(http://www.kde-look.org/CONTENT/content-files/109367-yasp-scripted-${pkgver}.tar.bz2)
md5sums=('b271abb634b6310ce7853a479ee682b0')

build() {
  cd $srcdir/yasp-scripted-$pkgver
  
  mkdir build && cd build
  cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` -DCMAKE_BUILD_TYPE=release ../ || return 1
  make DESTDIR="$pkgdir/" install || return 1
}

package() {
  cd $srcdir/yasp-scripted-$pkgver

  install -Dm644 README.syntax "$pkgdir/usr/share/doc/yasp-scripted/README.syntax"
  install -d -m755 "$pkgdir/usr/share/doc/yasp-scripted/yasp_scripts"
  install -d -m755 "$pkgdir/usr/share/doc/yasp-scripted/yasp_scripts/duncan-yasps-scripts"
  install -m644 yasp_scripts/*.script "$pkgdir/usr/share/doc/yasp-scripted/yasp_scripts"
  install -m644 yasp_scripts/duncan-yasps-scripts/* "$pkgdir/usr/share/doc/yasp-scripted/yasp_scripts/duncan-yasps-scripts"
}