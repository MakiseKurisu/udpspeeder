# Maintainer: Equim <sayaka@ekyu.moe>

pkgname=udpspeeder
_realname=UDPspeeder
pkgver=20210116.0
pkgrel=1
pkgdesc='Improve your Network Quality on a High-latency Lossy Link by using Forward Error Correction'
arch=('i686' 'x86_64' 'aarch64')
url="https://github.com/wangyu-/UDPspeeder"
license=('MIT')
depends=('gcc-libs')
source=("$pkgname-$pkgver.tar.gz::https://github.com/wangyu-/UDPspeeder/archive/refs/tags/$pkgver.tar.gz")
sha256sums=('657ae24dfd592a1f6f114342231b24d09baec712957969f425477b9f9fd5994a')

prepare() {
  cd "$_realname-$pkgver"
  touch git_version # disable make target
  echo 'const char * const gitversion = "'$pkgver'";' > git_version.h
  sed -i 's/-ggdb//' makefile
  sed -i 's/-static//' makefile
}

build() {
  cd "$_realname-$pkgver"
  make
}

package() {
  cd "$_realname-$pkgver"
  install -Dm755 speederv2 "$pkgdir/usr/bin/speederv2"
  install -Dm644 LICENSE.md "$pkgdir/usr/share/licenses/udpspeeder-git/LICENSE.md"
}
