# Maintainer: Luka Perkov <luka.perkov@sartura.hr>

pkgname=ustream-ssl-git
_gitname=ustream-ssl
pkgver=r45.a4ca615
# commit 0966435353d08f6644b65ac22a0b284f17c5787e
pkgrel=1
pkgdesc='library for SSL over ustream'
url='http://nbd.name/gitweb.cgi?p=ustream-ssl.git'
arch=('i686' 'x86_64')
license=('ISC BSD-3c')
depends=('libubox-lua-git' 'mbedtls')
makedepends=('git' 'cmake' 'gcc' 'make')
conflicts=('ustream-ssl')
provides=('ustream-ssl')
source=('git://nbd.name/ustream-ssl.git')
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/$_gitname"

	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/$_gitname"

	cmake CMakeLists.txt \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DPOLARSSL=ON \

	make
}

package() {
	cd "$srcdir/$_gitname"

	make DESTDIR="$pkgdir" install
}

# burp -c lib `ls ustream-ssl-git*.src.tar.gz | sort | tail -n 1`
