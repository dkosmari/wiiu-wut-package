_pkgname=wut
_branch=devel
pkgname=${_pkgname}-dkosmari-git
conflicts=(${_pkgname})
provides=(${_pkgname})
pkgver=1.9.1.r4.g84230bb
pkgrel=1
pkgdesc="Open-source Wii U Toolchain libraries."
arch=('any')
url="https://github.com/dkosmari/wut"
license=('zlib')
groups=('wiiu-dev')

depends=('devkitPPC' 'wut-tools')

options=(!buildflags !strip staticlibs)

source=("${_pkgname}::git+https://github.com/dkosmari/wut.git#branch=${_branch}")

pkgver() {
    cd "${srcdir}/${_pkgname}"
    WUT_VER=$(git describe --tags)
    WUT_MAJOR=$(echo "$WUT_VER" | sed "s/^v\([0-9]*\).*/\1/")
    WUT_MINOR=$(echo "$WUT_VER" | sed "s/^v[0-9]*\.\([0-9]*\).*/\1/")
    WUT_PATCH=$(echo "$WUT_VER" | sed "s/^v[0-9]*\.[0-9]*\.\([0-9]*\).*/\1/")
    WUT_SUFFIX=$(echo "$WUT_VER" | sed "s/^v[0-9]*\.[0-9]*\.[0-9]*-\(.*\)/\1/")
    printf "%d.%d.%d.r%s" "$WUT_MAJOR" "$WUT_MINOR" "$WUT_PATCH" "${WUT_SUFFIX/-/.}"
}

build() {
    cd "${srcdir}/${_pkgname}"

    make V=1
}

package() {
    cd "${srcdir}/${_pkgname}"

    make install DESTDIR="${pkgdir}"
}

sha256sums=('SKIP')
