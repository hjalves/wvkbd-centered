# Based on the AUR wvkbd PKGBUILD (Ash, Aren), plus a centred dock mode.
pkgname=wvkbd-centered
_pkgname=wvkbd
pkgver=0.21
pkgrel=1
pkgdesc='On-screen keyboard for wlroots (with --dock center)'
url='https://git.sr.ht/~proycon/wvkbd'
arch=('x86_64' 'i686' 'armv7h' 'aarch64')
license=('GPL3')
depends=('wayland' 'pango' 'cairo' 'glibc')
makedepends=('fontconfig' 'libxkbcommon' 'scdoc')
provides=("$_pkgname=$pkgver")
conflicts=("$_pkgname")
source=("$_pkgname-$pkgver.tar.gz::https://git.sr.ht/~proycon/wvkbd/archive/v$pkgver.tar.gz"
        'center-dock.patch')
sha512sums=('891eeb14ba7c93a08e6dac8d534656d0ca67f150b3d9bd51da51186f8a4637c68d412a1091aba0449bac7da43afabcef00355dba0d6ddaaacc241b604be14bb1'
            '5f29c07bc31be0c4925cf91be01d30586518ff8d9b5d719f8c7bff306364c0445ff92e054c39ad1dd3c13b01aaf89807f9bb442ea9817b781388f9bab18221d2')

prepare() {
  patch -d "$_pkgname-v$pkgver" -p1 < center-dock.patch
}

build() {
  make -C "$_pkgname-v$pkgver"
}

package() {
  make -C "$_pkgname-v$pkgver" PREFIX=/usr DESTDIR="$pkgdir" install
}
