# Maintainer: Dustin Bensing <dustin dot bensing at googlemail dot com>
# Contributor: Kristjan Reinloo <mail at kreinloo dot net>
_gitname=vmime
pkgname="lib${_gitname}-git"
pkgver=r1023.23fc354
pkgrel=1
pkgdesc="A powerful C++ class library for working with RFC-822 and MIME messages."
arch=("i686" "x86_64")
url="http://www.vmime.org/"
license=("GPL3")
depends=("gsasl" "icu")
makedepends=("cmake" "git")
conflicts=("libvmime" "libvmime-svn" "zarafa-libvmime")
optdepends=("sendmail: sendmail protocol support")
source=("${_gitname}::git://github.com/kisli/vmime.git")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/${_gitname}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "${srcdir}/${_gitname}"

  cmake -DVMIME_HAVE_MESSAGING_PROTO_SENDMAIL:BOOL=OFF \
        -DCMAKE_INSTALL_PREFIX:PATH=/usr \
	-DVMIME_INSTALL_LIBDIR=/usr/lib \
	-DVMIME_SHARED_PTR_USE_CXX=ON \
	-DVMIME_SHARED_PTR_USE_BOOST=OFF \
	-DVMIME_BUILD_SAMPLES=OFF
  make
}

package() {
  cd "${srcdir}/${_gitname}"
  make DESTDIR="${pkgdir}" install
}
