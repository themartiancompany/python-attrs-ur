# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

_py="python"
_pkg="attrs"
pkgname="${_py}-${_pkg}"
pkgver=23.1.0
_commit=1e2f6f9cac5cc60f0adab051c14adf09ffe39155
pkgrel=1
pkgdesc="Attributes without boilerplate."
arch=(
  'any'
)
license=(
  'MIT'
)
url="https://www.${_pkg}.org"
depends=(
  'python'
)
makedepends=(
  'git'
  'python-build'
  'python-installer'
  'python-hatchling'
  'python-hatch-vcs'
  'python-hatch-fancy-pypi-readme')

checkdepends=(
  'python-pytest'
  'python-cloudpickle'
  'python-hypothesis'
  'python-zope-interface'
)
_http="https://github.com"
_ns="${pkgname}"
_url="${_http}/${pkgname}/${_pkg}"
source=(
  "git+${_url}.git#commit=$_commit"
)
sha512sums=(
  'SKIP'
)

build() {
  cd \
    "${_pkg}"
  "${_py}" \
    -m \
      build \
    -nw
}

check() {
  cd \
    "${_pkg}"
  "${_py}" \
    -m installer
    --destdir=tmp_install \
    dist/*.whl
  # I am starting to think we should generate
  # python packages automatically
  PYTHONPATH="$PWD/tmp_install/usr/lib/python3.11/site-packages" \
  pytest
}

package() {
  cd \
    "${_pkg}"
  "${_py}" \
    -m installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim:set sw=2 sts=-1 et:
