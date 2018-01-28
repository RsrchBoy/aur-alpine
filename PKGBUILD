# -*- shell-script -*-
#
# Contributor: Adrian C. <anrxc..sysphere.org>

pkgname=alpine
pkgver=2.21
pkgrel=199
pkggit=0473711
arch=("i686" "x86_64")
pkgdesc="Apache licensed PINE mail user agent"
url="http://repo.or.cz/alpine.git"
license=("APACHE")
depends=("libldap" "krb5" "gettext")
optdepends=("aspell: for spell-checking support"
	    "hunspell: for spell-checking support"
            "topal: glue program that links GnuPG and alpine")
provides=("pine")
conflicts=("pine" "re-alpine")
replaces=("pine")
options=("!makeflags")
source=(alpine-0473711.patched.tar.gz)
md5sums=('5614336c36384d260f1773ee2afc4f02')

build() {
  cd "${srcdir}/${pkgname}-${pkggit}.patched"

# Configure Alpine
  LIBS+="-lpam -lkrb5 -lcrypto" ./configure --prefix=/usr \
  --with-passfile=.pine-passfile --without-tcl --disable-shared \
  --with-system-pinerc=/etc/${pkgname}.d/pine.conf \
  --with-system-fixed-pinerc=/etc/${pkgname}.d/pine.conf.fixed

# Build Alpine
  make
}


package() {
  cd "${srcdir}/${pkgname}-${pkggit}.patched"

# Install Alpine
  make DESTDIR="${pkgdir}" install
}
