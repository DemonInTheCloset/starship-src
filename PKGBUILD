# Maintainer: DemonInTheCloset

pkgname="starship-src"
_pkgname="starship"
pkgver=1.11.0
pkgrel=1
pkgdesc="The cross-shell prompt for astronauts"
arch=("x86_64" "armv7h" "aarch64")
url="https://github.com/starship/starship"
license=("ISC")
depends=()
optdepends=('powerline-fonts: powerline symbols for terminals'
            'nerd-fonts-complete: popular collections such as Font Awesome & fonts such as Hack')
makedepends=("cargo")
provides=("starship")
conflicts=("starship")
source=("$_pkgname-$pkgver.tar.gz::https://github.com/starship/starship/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('7b408ef8a2ab47d7a7d0e120889bf12c8f2a965796f8a027d8b2176287fdec6b')

build() {
    cd "$srcdir/$_pkgname-$pkgver"
    cargo build --release --locked --all-features --target-dir=target
}

check() {
    cd "$srcdir/$_pkgname-$pkgver"
    cargo test --release --locked --target-dir=target
}

package() {
    cd "$srcdir/$_pkgname-$pkgver"
    install -Dm755 target/release/$_pkgname "$pkgdir/usr/bin/$_pkgname"
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
