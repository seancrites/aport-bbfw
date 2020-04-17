# Contributor: Sean Crites <Sean.Crites@gmail.com>
# Maintainer: Sean Crites <Sean.Crites@gmail.com>
pkgname="bbfw"
pkgver="0.19.0"
pkgrel=20
pkgdesc="Firewall script to manage seperate domain, cluster and application filters via ipset & iptables"
url="https://github.com/bindle/bbfw"
arch="noarch"
repo=""
license="Modified BSD License"
depends="ipset iptables ip6tables"
subpackages="$pkgname-doc"
options="!check" # No upstream test-suite
source="https://github.com/bindle/bbfw/releases/download/v0.19/bbfw-0.19.0.tar.xz
	bbfw.initd"
builddir="$srcdir"/$pkgname-$pkgver

prefix_dir="/usr"

build() {

	cd "$builddir"

	./configure \
		--prefix="$prefix_dir" \
		--disable-slackware \
		--disable-initd \
		--disable-systemd

	make all

}

package() {

	cd "$builddir"

	make DESTDIR="$pkgdir" install

	install -Dm755 "$srcdir"/bbfw.initd "$pkgdir"/etc/init.d/bbfw

	/bin/sed -i "s|@prefix_dir@|$prefix_dir|" "$pkgdir"/etc/init.d/bbfw

}

sha512sums="236b4bd009fdf45534c13a950b82ac9e709d3a61475b7dfe508c4b1011e6006ee1bc2be56324d4252151b43479211883c98acac0b212bcd7bbf94cf04199d76f  bbfw-0.19.0.tar.xz
ba2ef6c7281e04336c89642dd2d3e18a819b0132623182ab3830dab859537103b62f07cdf701c15801b71caf37112691f6ef6dbfd0aaa1c3631a76215e9d21b4  bbfw.initd"
