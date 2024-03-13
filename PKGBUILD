# Maintainer: Mahdi Sarikhani <mahdisarikhani@outlook.com>
# Contributor: redfish <redfish@galactica.pw>
# Contributor: Gergely Imreh <imrehg@gmailcom>
# Contributor: Jakub "Kubuxu" Sztandera  <kubuxu@protonmail.ch>

pkgname=ipget
pkgver=0.10.0
pkgrel=1
pkgdesc="wget for IPFS: retrieve files over IPFS and save them locally"
arch=('x86_64')
url="https://github.com/ipfs/ipget"
license=('MIT')
depends=('glibc')
makedepends=('go')
optdepends=('go-ipfs: to use full potential of IPFS network')
options=('strip' 'lto' '!debug')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/ipfs/${pkgname}/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('a9bffe36f23284fa691cca0bc85d1890782ca0c7bc69a25f9881b712914a96cb')

build() {
  cd "${pkgname}-${pkgver}"
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export CGO_LDFLAGS="${LDFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -ldflags=-s -ldflags=-w -mod=readonly -modcacherw"
  go build
}

package() {
  cd "${pkgname}-${pkgver}"
  mkdir -m755 -p "${pkgdir}/usr/bin"
  install -Dm755 -t "${pkgdir}/usr/bin" ipget
  install -Dm644 -t "${pkgdir}/usr/share/licenses/${pkgname}" LICENSE
}

# vim: set expandtab ts=2 sw=2:
