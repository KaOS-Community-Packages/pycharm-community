pkgname=pycharm-community
pkgver=5.0
pkgrel=1
pkgdesc="Powerful Python and Django IDE. Community edition."
arch=('x86_64')
options=('!strip')
url="http://www.jetbrains.com/pycharm/"
license=('Apache')
depends=('java-environment>=6' 'giflib' 'qarma')
source=("http://download.jetbrains.com/python/$pkgname-$pkgver.tar.gz"
        'pycharm-community.desktop' )
sha512sums=('506c2675975209ee7bba16186996e26332f45981964d4642e6ce948829833f8e37067651a133f3216d192a4a16acd86c71458ca936bd84b0785e2d66c5968edd'
            'e708ffedc379a51e509eafa1abd30bbfaa3def02961b027d87b15093e4d9e07cdbd4e427245f5c135b5a2be6c88516882abbddb41fe907e8289f53812d7a8281')

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
