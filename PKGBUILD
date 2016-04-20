pkgname=mathmod
pkgver=4.1.80
_branch=283
pkgrel=1
pkgdesc="A mathematical modeling software"
arch=("x86_64")
url="https://sourceforge.net/projects/mathmod/"
license=('LGPL3')
depends=('qt5-base' 'qt5-tools' 'glu')
source=("$pkgname-$pkgver::https://sourceforge.net/code-snapshots/svn/m/ma/mathmod/branches/mathmod-branches-${_branch}-trunk.zip" "$pkgname.desktop")
md5sums=('4b6b2576ae739becd0fc4f187ec1b85c'
         '42efefc32753c8c03ae6c4e93e18d841')



build() {
  cd $srcdir/$pkgname-branches-${_branch}-trunk
  qmake-qt5
  make
}

package() {
  install -d -m 755 $pkgdir/usr/share/$pkgname
  cp -a $srcdir/$pkgname-branches-${_branch}-trunk/MathMod $pkgdir/usr/share/$pkgname/

  install -d -m 755 $pkgdir/usr/share/pixmaps
  cp -a $srcdir/$pkgname-branches-${_branch}-trunk/icon/catenoid_mini_64x64.png $pkgdir/usr/share/pixmaps/$pkgname.png

  install -d -m 755 $pkgdir/usr/share/applications
  cp -a $srcdir/$pkgname.desktop $pkgdir/usr/share/applications/


  install -d -m 755 "$pkgdir/usr/bin"
  echo -en "#!/bin/bash\nexec /usr/share/$pkgname/MathMod $@"  >"$pkgdir/usr/bin/mathmod"
    chmod +x  "$pkgdir/usr/bin/mathmod"

  rm -rf $pkgdir/usr/share/$pkgname/icon

}
