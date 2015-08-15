 
# Maintainer: Jens Staal <staal1978@gmail.com>

pkgname=gich
pkgver=20120526
pkgrel=1
pkgdesc="A cross platform which utility written in Go."
arch=('i686' 'x86_64')
license=('BSD')
url="https://bitbucket.org/jpoirier/gich"
depends=('go')
makedepends=('mercurial')


_gourl=bitbucket.org/jpoirier/gich

build() {
  cd "$srcdir"
  GOPATH="$srcdir" go get -fix -v -x ${_gourl}
}

check() {
  source /etc/profile.d/go.sh
  GOPATH="$GOPATH:$srcdir" go test -v -x ${_gourl}/...
}

package() {
  source /etc/profile.d/go.sh
  mkdir -p "${pkgdir}/usr/bin"
  install -p -m755 ${srcdir}/bin/* "$pkgdir/usr/bin"

  mkdir -p "$pkgdir/$GOPATH"
  cp -Rv --preserve=timestamps ${srcdir}/{src,pkg} "$pkgdir/$GOPATH"

# getting rid of contaminating library files... A better way to do it?
# a disadvantage now is that the source distribution of the package gets lost.
  rm -rf $pkgdir/usr/lib
}
