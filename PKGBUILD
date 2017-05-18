# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-attrs
pkgname=('python-attrs' 'python2-attrs')
pkgver=17.1.0
pkgrel=1
pkgdesc="Attributes without boilerplate."
arch=('any')
license=('MIT')
url="https://attrs.readthedocs.org/"
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-pytest-runner' 'python2-pytest-runner' 'python-zope-interface'
              'python2-zope-interface' 'python-hypothesis' 'python2-hypothesis')
source=("https://pypi.io/packages/source/a/attrs/attrs-$pkgver.tar.gz")
sha512sums=('5d902dfefdcfdc693931e0600833d3bc412d26026fda8691cc8f2652b4e872dfd17ac600a463c11152df11db1c9bbf6e598360d1ead50d9ebf5bae4124921517')

prepare() {
  cp -a attrs-$pkgver{,-py2}
}

build() {
  cd "$srcdir"/attrs-$pkgver
  python setup.py build
 
  cd "$srcdir"/attrs-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/attrs-$pkgver
  python setup.py pytest

  cd "$srcdir"/attrs-$pkgver-py2
  python2 setup.py pytest
}
 
package_python-attrs() {
  depends=('python')
 
  cd attrs-$pkgver
  python setup.py install --root="$pkgdir" --optimize=1 --skip-build
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
 
package_python2-attrs() {
  depends=('python2')
 
  cd attrs-$pkgver-py2
  python2 setup.py install --root="$pkgdir" --optimize=1 --skip-build
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
