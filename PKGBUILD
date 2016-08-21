pkgname=pycharm-community
pkgver=2016.2.1
pkgrel=1
pkgdesc="Powerful Python and Django IDE. Community edition."
arch=('x86_64')
options=('!strip')
url="http://www.jetbrains.com/pycharm/"
license=('Apache')
depends=('java-environment>=6' 'giflib' )
source=("http://download.jetbrains.com/python/$pkgname-$pkgver.tar.gz"
        'pycharm-community.desktop' )
sha256sums=('76a5d58a6ecbafa48abde9823948f0614472ecbc0535c639ceb593569a1e06a7'
            '446134e5ef3012a6f19549d63fb3e18f07cdd00b39cd67fec99af9338a594f1e')


package() {
  cd $srcdir
  mkdir -p $pkgdir/opt/$pkgname
  cp -R $srcdir/$pkgname-$pkgver/* $pkgdir/opt/$pkgname

  echo '-Dawt.useSystemAAFontSettings=on' >> $pkgdir/opt/$pkgname/bin/pycharm64.vmoptions
  echo '-Dswing.aatext=true' >> $pkgdir/opt/$pkgname/bin/pycharm64.vmoptions

  mkdir -p $pkgdir/usr/share/{applications,pixmaps}
  install -Dm644 $startdir/pycharm-community.desktop $pkgdir/usr/share/applications/
  install -Dm644 $pkgdir/opt/$pkgname/bin/pycharm.png $pkgdir/usr/share/pixmaps/pycharm.png

  mkdir -p $pkgdir/usr/bin
  ln -s /opt/pycharm-community/bin/pycharm.sh $pkgdir/usr/bin/pycharm
}
