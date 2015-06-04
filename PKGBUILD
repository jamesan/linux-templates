# Maintainer: James An <james@jamesan.ca>

# PKGBUILD
# template for writing a PKGBUILD file

# Copyright 2014 James An

# THIS PROGRAM is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

pkgname=TODO
pkgver=TODO
pkgrel=1
pkgdesc="TODO"
arch=('i686' 'x86_64' 'any')
url="http://TODO"
license=('GPL')
depends=('TODO')
makedepends=('git')
provides=($pkgname)
conflicts=($pkgname)
options=()
install=TODO.install
source=($pkgname-$pkgver.tar.gz
        $pkgname-$pkgver.patch)
md5sums=()

prepare() {
    cd $pkgname-$pkgver
    # cd $pkgname
    # cd $pkgver

    # Apply all patches to the source code root directory
    for file in ../*.patch; do
        patch -p1 -i $file
    done
}

build() {
    cd $pkgname-$pkgver
    # cd $pkgname
    # cd $pkgver

    ./autogen.sh --prefix=/usr
    make
}

check() {
    cd $pkgname-$pkgver
    # cd $pkgname
    # cd $pkgver

    make -k check
}

package() {
    cd $pkgname-$pkgver
    # cd $pkgname
    # cd $pkgver

    make DESTDIR="$pkgdir/" install

    # pruning unnecessary files
    rm -rf "$pkgdir/etc/rc.d"
    rm -rf "$pkgdir/etc/init.d"

    # installing package into opt
    install -m755 -d "$pkgdir/opt"
    cp -R "$pkgname" "$pkgdir/opt/"

    # installing doc files
    install -m755 -d "$pkgdir/usr/share/doc/$pkgname"
    cp -R doc/* "$pkgdir/usr/share/doc/$pkgname"

    # installing the license
    install -D -m644 LICENSE*d "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

    # correct file permissions (disabling file execution)
    find "$pkgdir" -type f -exec chmod 0644 {} +
    find "$pkgdir" -type d -exec chmod 0755 {} +
}
