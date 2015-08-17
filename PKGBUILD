# Mantainer: Alex Talker <alextalker at openmailbox dot org>

pkgname=qupzilla-qt5-qtwebkit-git
pkgver=v1.8.6.r1.ga0de5dc
pkgrel=1
pkgdesc="A new and very fast open source browser based on WebKit core, written in Qt Framework."
arch=('i686' 'x86_64')
url="http://qupzilla.com/index.php"
license=('GPL')
depends=( 'qt5-base' 'qt5-script' 'qt5-webkit')
makedepends=('git')
provides=('qupzilla' 'qupzilla-git')
conflicts=('qupzilla' 'qupzilla-git' 'qupzilla-qt5-git')
source=(qupzilla::'git+https://github.com/QupZilla/qupzilla.git#branch=v1.8')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/qupzilla"
  git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/qupzilla"
  export USE_WEBGL="true"
  export KDE_INTEGRATION="true"
  export QUPZILLA_PREFIX="/usr/"
   
  qmake-qt5
  make clean
  make
}

package() {
  cd ${srcdir}/qupzilla
  make INSTALL_ROOT="$pkgdir/" install
}
