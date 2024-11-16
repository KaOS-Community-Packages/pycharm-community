pkgname=pycharm-community
pkgver=2024.3
pkgrel=1
_pkgdir=${pkgname}-${pkgver}
pkgdesc="Powerful Python and Django IDE. Community edition."
arch=('x86_64')
options=('!strip')
url="http://www.jetbrains.com/pycharm/"
license=('Apache')
source=("http://download.jetbrains.com/python/${pkgname}-${pkgver}.tar.gz"
        'pycharm-community.desktop')
md5sums=('d53e084703a3f068163574a54fd36a2f'
         '99ac487202a427060a9956ffa2e34a06')

package() {
    install -dm 755 ${pkgdir}/opt/
    install -dm 755 ${pkgdir}/usr/bin/
    install -dm 755 ${pkgdir}/usr/share/applications/
    install -dm 755 ${pkgdir}/usr/share/icons/hicolor/scalable/apps/
    
    python3 ${_pkgdir}/plugins/python-ce/helpers/pydev/setup_cython.py build_ext --inplace
        
#    rm -rf ${_pkgdir}/jbr # DO NOT COMMIT IF UNCOMMENTED, only if you have installed jdk/openjdk version >= 17 in your system
    rsync -rtl "${_pkgdir}"/ ${pkgdir}/opt/${pkgname}

    ln -s /opt/${pkgname}/bin/pycharm.sh ${pkgdir}/usr/bin/pycharm
    install -Dm 644 ${srcdir}/${pkgname}.desktop ${pkgdir}/usr/share/applications/
    install -Dm 644 ${pkgdir}/opt/${pkgname}/bin/pycharm.svg ${pkgdir}/usr/share/icons/hicolor/scalable/apps/pycharm.svg
}
