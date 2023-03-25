# Maintainer: Pawel Bogut <pbogut@pbogut.me>

pkgname=headshotbox
pkgver=0.18.2
pkgrel=1
epoch=1
pkgdesc="Headshot Box generates statistics for your Counter-Strike: Global Offensive matches."
arch=('any')
url="https://github.com/bugdone/headshotbox"
license=('MIT')
depends=(
)
install=headshotbox.install


optdepends=()
source=(${url}/releases/download/${pkgver}/headshotbox-${pkgver}-linux.zip
        headshotbox.service
        headshotbox.sh)
sha512sums=('f1d21c69e8ff13eb7694a39d10b19e15bf821cda82c827b7e4c2400fa357cab13797341daa8284b84aee6c742d56f273bf69e0a4684f49225efc275a507c3208'
            'c8414a71d82c024cf223557ffdfe2b3a9d4398298d5b83960b51c668fc8042718d33c491783dd08ccaeee232915566943138b811b1b2a0dd7790be1fae8af2f8'
            '0b7b2f81ca7525c122b105d5a2c4226c7ad58ff243794e6c3538fff8bbe504dcf5ac81e276f1aa5c705fa5bc5c08c4c1db9d4aa0f1d026618bcd88c3d566eebb')


build() {
  sed -i "s/PKG_VERSION/${pkgver}/g" headshotbox.sh
}

package() {
  _pkg="headshotbox-${pkgver}-linux"
  _jar="hsbox-${pkgver}-standalone.jar"
  install -d "$pkgdir"/usr/share/headshotbox

  install -m755 "${srcdir}/${_pkg}/demoinfogo" "${pkgdir}/usr/share/headshotbox/demoinfogo"
  install -m755 "${srcdir}/${_pkg}/headshotbox.sh" "${pkgdir}/usr/share/headshotbox/headshotbox.sh"
  install -m755 "${srcdir}/headshotbox.sh" "${pkgdir}/usr/share/headshotbox/headshotbox-p.sh"
  install -m644 "${srcdir}/${_pkg}/${_jar}" "${pkgdir}/usr/share/headshotbox/${_jar}"

  cp -r "${srcdir}/${_pkg}/libs" "${pkgdir}/usr/share/headshotbox/"

  install -m0644 -D headshotbox.service "${pkgdir}/etc/systemd/user/headshotbox.service"
  install -m0644 -D headshotbox.service "${pkgdir}/etc/systemd/user/headshotbox@.service"
}
