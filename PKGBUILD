pkgname=pycharm-community
pkgver=2023.3.1
pkgrel=1
_pkgdir=${pkgname}-${pkgver}
pkgdesc="Powerful Python and Django IDE. Community edition."
arch=('x86_64')
options=('!strip')
url="http://www.jetbrains.com/pycharm/"
license=('Apache')
source=("http://download.jetbrains.com/python/${pkgname}-${pkgver}.tar.gz"
        'pycharm-community.desktop')
md5sums=('b07c29c58375917da7c256d4e6c5599c'
         '99ac487202a427060a9956ffa2e34a06')

package() {
    install -dm 755 ${pkgdir}/opt/
    install -dm 755 ${pkgdir}/usr/bin/
    install -dm 755 ${pkgdir}/usr/share/applications/
    install -dm 755 ${pkgdir}/usr/share/icons/hicolor/scalable/apps/
    
    cd ${srcdir}
    python3 ${_pkgdir}/plugins/python-ce/helpers/pydev/setup_cython.py build_ext --inplace
        
    rsync -rtl "${_pkgdir}"/ ${pkgdir}/opt/${pkgname}
    sed -i 's/lcd/on/' ${pkgdir}/opt/${pkgname}/bin/pycharm64.vmoptions
    echo -e "-Dswing.aatext=true\n-Dfile.encoding=UTF-8" >> ${pkgdir}/opt/${pkgname}/bin/pycharm64.vmoptions

    install -Dm644 ${srcdir}/pycharm-community.desktop ${pkgdir}/usr/share/applications/
    install -Dm 644 ${pkgdir}/opt/${pkgname}/bin/pycharm.svg ${pkgdir}/usr/share/icons/hicolor/scalable/apps/pycharm.svg
    ln -s /opt/pycharm-community/bin/pycharm.sh ${pkgdir}/usr/bin/pycharm
}
