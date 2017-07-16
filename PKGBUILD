pkgname=pycharm-community
pkgver=2017.1.5
pkgrel=1
pkgdesc="Powerful Python and Django IDE. Community edition."
arch=('x86_64')
options=('!strip')
url="http://www.jetbrains.com/pycharm/"
license=('Apache')
depends=('openjdk' 'giflib')
source=("http://download.jetbrains.com/python/${pkgname}-${pkgver}.tar.gz"
        'pycharm-community.desktop'
        'pycharm.svg')
md5sums=('27059f2d7841746490bf855db3923b75'
         '7e6e1f9786e55bbee3efe73b91f3684e'
         'dc869b1bb321c7a9895192de2e0d56d3')

package() {
    mkdir -p ${pkgdir}/opt/${pkgname}
    mkdir -p ${pkgdir}/usr/share/{applications,icons/hicolor}
    mkdir -p ${pkgdir}/usr/bin
    
    cd ${srcdir}
    python2 ${pkgname}-${pkgver}/helpers/pydev/setup_cython.py build_ext --inplace
    python3 ${pkgname}-${pkgver}/helpers/pydev/setup_cython.py build_ext --inplace
    rm -rf ${pkgname}-${pkgver}/jre64
    
    cp -R ${pkgname}-${pkgver}/* ${pkgdir}/opt/${pkgname}
    sed -i 's/lcd/on/' ${pkgdir}/opt/${pkgname}/bin/pycharm64.vmoptions
    echo '-Dswing.aatext=true' >> ${pkgdir}/opt/${pkgname}/bin/pycharm64.vmoptions

    install -Dm644 ${srcdir}/pycharm-community.desktop ${pkgdir}/usr/share/applications/
    install -Dm644 ${srcdir}/pycharm.svg ${pkgdir}/usr/share/icons/hicolor/scalable/apps/pycharm.svg
    rm ${pkgdir}/opt/${pkgname}/bin/pycharm.png

    ln -s /opt/pycharm-community/bin/pycharm.sh ${pkgdir}/usr/bin/pycharm
}
