pkgname=pycharm-community
pkgver=2022.3.2
pkgrel=1
pkgdesc="Powerful Python and Django IDE. Community edition."
arch=('x86_64')
options=('!strip')
url="http://www.jetbrains.com/pycharm/"
license=('Apache')
source=("http://download.jetbrains.com/python/${pkgname}-${pkgver}.tar.gz"
        'pycharm-community.desktop')
md5sums=('dcaf746d38ba0582d830aeba63f26ec7'
         '99ac487202a427060a9956ffa2e34a06')

package() {
    mkdir -p ${pkgdir}/opt/${pkgname}
    mkdir -p ${pkgdir}/usr/share/{applications,icons/hicolor}
    mkdir -p ${pkgdir}/usr/bin
    
    cd ${srcdir}
    python3 ${pkgname}-${pkgver}/plugins/python-ce/helpers/pydev/setup_cython.py build_ext --inplace
        
    cp -R ${pkgname}-${pkgver}/* ${pkgdir}/opt/${pkgname}
    sed -i 's/lcd/on/' ${pkgdir}/opt/${pkgname}/bin/pycharm64.vmoptions
    echo '-Dswing.aatext=true' >> ${pkgdir}/opt/${pkgname}/bin/pycharm64.vmoptions

    install -Dm644 ${srcdir}/pycharm-community.desktop ${pkgdir}/usr/share/applications/
    install -Dm 644 ${pkgdir}/opt/${pkgname}/bin/pycharm.svg ${pkgdir}/usr/share/icons/hicolor/scalable/apps/pycharm.svg
    ln -s /opt/pycharm-community/bin/pycharm.sh ${pkgdir}/usr/bin/pycharm
}
