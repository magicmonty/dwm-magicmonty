# Maintainer: Martin Gondermann (magicmonty) <magicmonty@pagansoft.de>
pkgname=dwm-magicmonty-git
pkgver=6.2.r14.897a867
pkgrel=1
pkgdesc="A customized build of dwm based on the build by DistroTube."
arch=(x86_64 i686)
url="https://github.com/magicmonty/dwm-magicmonty.git"
license=('MIT')
groups=()
depends=(libx11 libxinerama ttf-hack ttf-joypixels freetype2 st dmenu libxft-bgra-git)
makedepends=(make)
checkdepends=()
optdepends=(surf)
provides=(dwm)
conflicts=(dwm)
replaces=()
backup=()
options=()
source=("git+$url")
noextract=()
md5sums=('SKIP')
validpgpkeys=()

pkgver() {
  cd "${_pkgname}"
  printf "6.2.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd dwm-magicmonty
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  cd dwm-magicmonty
  mkdir -p ${pkgdir}/opt/${pkgname}
  cp -rf * ${pkgdir}/opt/${pkgname}
  make PREFIX=/usr DESTDIR="${pkgdir}" install
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/dwm-magicmonty/LICENSE"
  install -Dm644 README.md "${pkgdir}/usr/share/doc/dwm-magicmonty/README.md"
  install -Dm644 "${srcdir}/dwm-magicmonty/dwm.desktop" "$pkgdir/usr/share/xsessions/dwm.desktop"
}

