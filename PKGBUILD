# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=ark-git
pkgver=22.03.70.r4652
pkgrel=1
pkgdesc='Archiving Tool'
arch=(x86_64)
url='https://apps.kde.org/ark/'
license=(GPL)
depends=(kparts-git kpty-git libarchive libzip kitemmodels-git hicolor-icon-theme)
makedepends=(extra-cmake-modules-git kdoctools-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('p7zip: 7Z format support' 'unrar: RAR decompression support' 'unarchiver: RAR format support'
            'lzop: LZO format support' 'lrzip: LRZ format support')
groups=(kde-applications-git kde-utilities-git)
source=("git+https://invent.kde.org/utilities/${pkgname%-git}")
sha256sums=('SKIP')


pkgver() {
  cd ${srcdir}/${pkgname%-git}
  _ver="$(cat CMakeLists.txt | grep RELEASE_SERVICE_VERSION | cut -d '"' -f2 | tr '\n' '.' | cut -d "." -f 1-3)"
  echo "$(echo ${_ver}).r$(git rev-list --count HEAD)"
}

build() { 
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

