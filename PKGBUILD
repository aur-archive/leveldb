# Maintainer: feydaykyn <feydaykyn@yahoo.fr>

#Changelog:
#18.08.2012 : Added gperftools as optional dep (thanks falconindy)
#13.08.2012 : Include folder and static lib now copied, arch is now "i686 x86_64" thanks to Thestinger comment

pkgname=leveldb
pkgver=1.5.0
pkgrel=5
pkgdesc="A fast and lightweight key/value database library by Google."
arch=(i686 x86_64)
url="https://code.google.com/p/leveldb/"
license=('BSD')
optdepends=('snappy: Data compression; you will have to rebuild leveldb', 'gperftools: Fast, multi-threaded malloc() and nifty performance analysis tools')
provides=('leveldb')
source=("https://leveldb.googlecode.com/files/$pkgname-$pkgver.tar.gz")
sha1sums=('b5b45ff74065f242c37f465b13dafb925972ca43')

build() {
	cd ${srcdir}/$pkgname-$pkgver
	make
}

package() {
	  mkdir -p $pkgdir/usr/lib
	  cp ${srcdir}/$pkgname-$pkgver/libleveldb.a $pkgdir/usr/lib
	  cp ${srcdir}/$pkgname-$pkgver/libleveldb.so.1.5 $pkgdir/usr/lib
	  cd $pkgdir/usr/lib
	  ln -s libleveldb.so.1.5 libleveldb.so.1
	  ln -s libleveldb.so.1.5 libleveldb.so
	  msg "Static and shared lib installed in /usr/lib"

	  mkdir -p $pkgdir/usr/include/$pkgname
	  cp -r ${srcdir}/$pkgname-$pkgver/include/* $pkgdir/usr/include/$pkgname/
	  msg "Include files installed in /usr/include/$pkgname"

	  mkdir -p $pkgdir/usr/share/licenses/$pkgname
	  cp ${srcdir}/$pkgname-$pkgver/LICENSE $pkgdir/usr/share/licenses/$pkgname/
	  msg "License installed in /usr/share/license/$pkgname"

	  mkdir -p $pkgdir/usr/share/doc/$pkgname
	  cp -r ${srcdir}/$pkgname-$pkgver/doc/* $pkgdir/usr/share/doc/$pkgname/
	  msg "Doc installed in /usr/share/doc/$pkgname"
}