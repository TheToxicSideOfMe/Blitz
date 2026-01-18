# Maintainer: Your Name <rayen.stark@protonmail.com>
pkgname=blitz
pkgver=0.1.0
pkgrel=1
pkgdesc="A modern GUI for xboxdrv to configure game controllers"
arch=('x86_64')
url="https://github.com/TheToxicSideOfMe/blitz"
license=('MIT')
depends=('webkit2gtk' 'gtk3' 'libappindicator-gtk3' 'xboxdrv' 'polkit')
makedepends=('rust' 'cargo' 'nodejs' 'pnpm')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('PUT_THE_ACTUAL_SHA256_HERE')

build() {
  cd "$pkgname-$pkgver"
  
  # Install node dependencies
  pnpm install
  
  # Build the Tauri app
  pnpm tauri build
}

package() {
  cd "$pkgname-$pkgver"
  
  # Install the binary
  install -Dm755 \
    src-tauri/target/release/blitz \
    "$pkgdir/usr/bin/blitz"

  # Install icons
  install -Dm644 \
    src-tauri/icons/32x32.png \
    "$pkgdir/usr/share/icons/hicolor/32x32/apps/blitz.png"

  install -Dm644 \
    src-tauri/icons/128x128.png \
    "$pkgdir/usr/share/icons/hicolor/128x128/apps/blitz.png"

  # Install desktop file
  install -Dm644 \
    blitz.desktop \
    "$pkgdir/usr/share/applications/blitz.desktop"
  
  # Install license
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}