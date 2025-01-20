# Maintainer: Bidski <bidskii@gmail.com>
# Contributor: László Várady <laszlo.varady93@gmail.com>

pkgname=openconnect-sso
pkgdesc="Wrapper script for OpenConnect supporting Azure AD (SAMLv2) authentication"
pkgver=0.8.1
pkgrel=1
arch=('any')
url="https://github.com/Bidski/openconnect-sso"
license=('GPL3')
depends=('python' 'python-pyqt6' 'python-pyqt6-webengine' 'python-attrs' 'python-colorama'
         'python-keyring' 'python-lxml' 'python-prompt_toolkit' 'python-pyxdg' 'python-requests'
         'python-structlog' 'python-toml' 'python-pysocks' 'python-jaraco.classes' 'sudo' 'openconnect')
makedepends=('python-poetry')
checkdepends=('python-pytest' 'python-pytest-asyncio' 'python-pyotp' 'python-pytest-httpserver')
source=("https://github.com/Bidski/${pkgname}/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('30574fcceb5ec1243abfb0a7ec105e5eace0d111d7fe4fd3851671b51b8efd8c')

build() { 
  cd "${pkgname}-${pkgver}"
  poetry build
}

check() {
  cd "${pkgname}-${pkgver}"
  pytest
}

package() {
  python -m installer --destdir="${pkgdir}" "${pkgname}-${pkgver}/dist/"*.whl

  install -Dm644 "${pkgname}-${pkgver}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
