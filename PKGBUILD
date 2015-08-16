# Maintainer: Jakub Klinkovský <kuba.klinkovsky@gmail.com>
# Contributor: Mark Foxwell <fastfret79@archlinux.org.uk>

pkgname=imapfilter-git
_pkgname=imapfilter
pkgver=v2.5.6.5.g3c49012
pkgrel=1
pkgdesc="A mail filtering utility for processing IMAP mailboxes"
url='https://github.com/lefcha/imapfilter'
arch=('i686' 'x86_64')
license=('MIT')
depends=('lua' 'pcre' 'openssl')
makedepends=('git')
conflicts=('imapfilter')
provides=('imapfilter')
source=('git://github.com/lefcha/imapfilter.git')
md5sums=('SKIP')

pkgver() {
  cd "$_pkgname"
  git describe --tags --always | sed 's|-|.|g'
}

build() {
  cd "$srcdir/$_pkgname"
  make PREFIX=/usr all
}

package() {
  cd "$srcdir/$_pkgname"

  make PREFIX=/usr DESTDIR="$pkgdir" MANDIR=/usr/share/man install

  # install sample files
  install -D -m644 samples/config.lua $pkgdir/usr/share/$_pkgname/samples/config.lua
  install -D -m644 samples/extend.lua $pkgdir/usr/share/$_pkgname/samples/extend.lua

  # install license
  install -D -m644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
