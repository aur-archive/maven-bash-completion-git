# Maintainer: FrozenCow <frozencow@gmail.com>
pkgname=maven-bash-completion-git
pkgver=20121120
pkgrel=1
pkgdesc="Provides bash completion for maven"
arch=(any)
url="https://github.com/juven/maven-bash-completion"
license=('GPL')
groups=()
depends=('maven>=3.0.4' 'bash-completion')
makedepends=('git')
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
source=()
noextract=()
md5sums=() #generate with 'makepkg -g'

_gitroot=git://github.com/juven/maven-bash-completion.git
_gitname=maven-bash-completion

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"
}

package() {
  cd "$srcdir/$_gitname-build"
  install -Dm644 bash_completion.bash "$pkgdir/etc/bash_completion.d/maven"
}

# vim:set ts=2 sw=2 et:
