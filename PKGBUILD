pkgname=qt6-qtimageformats
pkgver=6.9.2
pkgrel=1
pkgdesc="Plugins for additional image formats: TIFF, MNG, TGA, WBMP"
arch=('x86_64')
url="https://www.qt.io"
license=(
    'GPL-3.0-only'
    'LGPL-3.0-only'
    'LicenseRef-Qt-Commercial'
    'Qt-GPL-exception-1.0'
)
depends=(
    'gcc-libs'
    'glibc'
    'jasper'
    'libmng'
    'libtiff'
    'libwebp'
    'qt6-qtbase'
)
makedepends=(
    'cmake'
    'git'
    'ninja'
)
source=(git+https://code.qt.io/qt/${pkgname#*-}#tag=v${pkgver})
sha256sums=(b1cb0c8cc44d7128e4ca41a98540e861cec3fa638016d3115b778e92f70dbf52)

build() {
    cd ${pkgname#*-}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D INSTALL_LIBDIR=lib64
        -D CMAKE_MESSAGE_LOG_LEVEL=STATUS
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build
}

package() {
    cd ${pkgname#*-}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
