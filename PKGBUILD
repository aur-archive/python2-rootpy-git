# Maintainer: Faruk Diblen <fdiblen at gmail dot com>

pkgname=python2-rootpy-git
pkgver=20121211
pkgrel=2
pkgdesc="A python module that provides a more feature-rich and pythonic interface with the ROOT libraries on top of the existing PyROOT bindings. Git version."
arch=(i686 x86_64)
url="http://rootpy.org"
license=('LGPL')
depends=('git' 'root' 'python2-numpy' 'python2-matplotlib' 'python2-pytables' 'readline')
optdepends=()
provides=('python2-rootpy-git')
#conflicts=('python2-rootpy-git')
md5sums=()

_gitroot="https://github.com/rootpy/rootpy.git"
_gitname=rootpy

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"

}

package() {
  cd "$srcdir/$_gitname-build"
  python2 setup.py install --root="$pkgdir"
}




