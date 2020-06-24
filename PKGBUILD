pkgname=devtools-arch4edu-extra
pkgver=10.ee349df
pkgrel=1
pkgdesc='Extra tools for arch4edu package maintainers'
arch=('any')
url='http://github.com/arch4edu/devtools-arch4edu-extra'
license=('GPL')
depends=('devtools')
makedepends=('git')
optdepends=('archlinuxarm-keyring')
source=("git+${url}.git")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  echo "$(git rev-list --count master).$(git rev-parse --short master)"
}

package() {
  cd "$srcdir/$pkgname"
  mkdir -p $pkgdir/usr/bin
  mkdir -p $pkgdir/usr/share/devtools

  for i in armv6h armv7h aarch64
  do
    cp $srcdir/$pkgname/pacman-extra-$i.conf $pkgdir/usr/share/devtools/
    cp $srcdir/$pkgname/makepkg-$i.conf $pkgdir/usr/share/devtools/
    ln -sf /usr/bin/archbuild $pkgdir/usr/bin/extra-$i-build
  done

  ln -sf /usr/bin/archbuild $pkgdir/usr/bin/arch4edu-x86_64-build
  cat /usr/share/devtools/pacman-extra.conf arch4edu.conf > $pkgdir/usr/share/devtools/pacman-arch4edu.conf
  cat /usr/share/devtools/pacman-extra.conf arch4edu.conf > $pkgdir/usr/share/devtools/pacman-multilib-arch4edu.conf
}
