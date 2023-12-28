pkgname=rojo
pkgver=7.2.1
pkgrel=1
pkgdesc="Rojo enables Roblox developers to use professional-grade software engineering tools"
arch=('x86_64')
url="https://github.com/rojo-rbx/rojo"
license=('MPL2')
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::https://static.crates.io/crates/$pkgname/$pkgname-$pkgver.crate")
sha256sums=('ec9849860b177d496bbf9f1df1b20eaa9ec5106a2ae3d540f6e76f576e8a6286')

prepare() {
	cd $pkgname-$pkgver
	export RUSTUP_TOOLCHAIN=stable
	cargo fetch --locked --target "$(rustc -vV | sed -n 's/host: //p')"
}

build() {
	cd $pkgname-$pkgver
	export RUSTUP_TOOLCHAIN=stable
	export CARGO_TARGET_DIR=target
	cargo build --frozen --release --all-features
}

check() {
	cd $pkgname-$pkgver
	export RUSTUP_TOOLCHAIN=stable
	cargo test --frozen --all-features
}

package() {
	cd $pkgname-$pkgver
	install -Dm0755 -t "$pkgdir/usr/bin/" "target/release/$pkgname"
}