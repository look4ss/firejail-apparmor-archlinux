pkgname=firejail-apparmor
pkgver=0.9.60
pkgrel=1
pkgdesc="Apparmor support for Firejail"
arch=('i686' 'x86_64')
url="https://firejail.wordpress.com/"
license=('GPL2')
depends=('apparmor')
provides=('firejail')
conflicts=('firejail')
backup=('etc/firejail/login.users'
	'etc/firejail/firejail.config'
	'etc/apparmor.d/local/firejail-local')
source=(${pkgname}-${pkgver}.tar.gz::https://github.com/netblue30/firejail/archive/$pkgver.tar.gz)
sha256sums=('dd3059b19365c2c095b85e3f86737fdcaca0a05357680f0e377bebf07791bc70')

build() {
	cd "${srcdir}/firejail-${pkgver}"
	# fix build
	export CFLAGS="${CFLAGS/-fsanitize=undefined/}"
	./configure --prefix=/usr --enable-apparmor
	make
}

package() {
	cd "${srcdir}/firejail-${pkgver}"
	make DESTDIR="${pkgdir}" install
}

