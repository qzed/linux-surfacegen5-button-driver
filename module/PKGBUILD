pkgname="surfacebook2-button-driver"
pkgver="0.1.0"
pkgrel=1
pkgdesc="Linux Driver for Surface Book 2/Surface Pro (2017) Power and Volume Buttons"
license=('GPL v2')
arch=('x86_64' 'i686')
depends=('dkms')

source=(
    "src::git+https://github.com/qzed/surfacebook2-linux-button-driver.git"
)

sha256sums=('SKIP')

package() {
    cd "${srcdir}/src"

    install -d "${pkgdir}/usr/src/sb2_button-${pkgver}/"
    cp -r "${srcdir}/src/"* "${pkgdir}/usr/src/sb2_button-${pkgver}/"

    install -Dm644 "${srcdir}/src/sb2_button.conf" "${pkgdir}/usr/lib/depmod.d/sb2_button.conf"
}
