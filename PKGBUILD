pkgname=pycharm-community
pkgver=4.0
pkgrel=5
pkgdesc="Powerful Python and Django IDE. Community edition."
arch=('x86_64')
options=('!strip')
url="http://www.jetbrains.com/pycharm/"
license=('Apache')
depends=('java-environment>=6' 'giflib')
source=(http://download.jetbrains.com/python/$pkgname-$pkgver.$pkgrel.tar.gz
        'pycharm-community.desktop' )
sha256sums=('315870d7691c5a716cb632b59acf7e3bed95667297a32e2708ffe0743501ca9a'
            '446134e5ef3012a6f19549d63fb3e18f07cdd00b39cd67fec99af9338a594f1e')
package() {
  cd $srcdir
  mkdir -p $pkgdir/opt/$pkgname
  cp -R $srcdir/$pkgname-$pkgver.$pkgrel/* $pkgdir/opt/$pkgname
  
  echo '-Dawt.useSystemAAFontSettings=on' >> $pkgdir/opt/$pkgname/bin/pycharm64.vmoptions
  echo '-Dswing.aatext=true' >> $pkgdir/opt/$pkgname/bin/pycharm64.vmoptions 

  mkdir -p $pkgdir/usr/share/{applications,pixmaps}
  install -Dm644 $startdir/pycharm-community.desktop $pkgdir/usr/share/applications/
  install -Dm644 $pkgdir/opt/$pkgname/bin/pycharm.png $pkgdir/usr/share/pixmaps/pycharm.png
  
  mkdir -p $pkgdir/usr/bin
  ln -s /opt/pycharm-community/bin/pycharm.sh $pkgdir/usr/bin/pycharm
}
