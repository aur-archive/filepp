# Maintainer: Sergey Rublev <narma.nsk@gmail.com>
pkgname=filepp
pkgver=1.8.0
pkgrel=1
pkgdesc="The generic file preprocessor"
arch=('any')
license=('GPL2')
depends=('perl')
url="http://www-users.york.ac.uk/~dm26/filepp/"
source=("${url}/filepp-${pkgver}.tar.gz")
md5sums=('b7ee96061cacef5a6a985b0be8c82801')

build() {
  cd "$srcdir/${pkgname}-${pkgver}"

  # datarootdir in Makefile doesn't use $prefix
  ./configure --prefix=/usr --datarootdir='${prefix}/share/'
  make
}

package() {
  cd "$srcdir/${pkgname}-${pkgver}"
  install -d $pkgdir/usr/bin
  make prefix=$pkgdir/usr install
  # datarootdir in Makefile doesn't use $prefix 
  sed -i -re 's/\$\{prefix\}/\/usr/' $pkgdir/usr/bin/filepp
}

