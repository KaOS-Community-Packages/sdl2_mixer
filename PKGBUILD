pkgname=sdl2_mixer
pkgver=2.0.1
pkgrel=1
pkgdesc="A simple multi-channel audio mixer (Version 2)"
arch=('x86_64')
url="http://www.libsdl.org/projects/SDL_mixer"
license=('MIT')
depends=('sdl2' 'libvorbis' 'libmodplug' 'smpeg' 'flac' 'fluidsynth')
source=("http://www.libsdl.org/projects/SDL_mixer/release/SDL2_mixer-${pkgver}.tar.gz")
md5sums=('c6c4f556d4415871f526248f5c9a627d')

prepare() {
  cd "${srcdir}/SDL2_mixer-${pkgver}/"

  sed -i "s|/etc/timidity|/etc/timidity++|g" timidity/config.h
  sed -i "s|/etc/timidity++.cfg|/etc/timidity++/timidity.cfg|g" timidity/config.h
}

build() {
  cd "${srcdir}/SDL2_mixer-${pkgver}/"

  export CFLAGS+=" ${CFLAGS} -I/usr/include/libmodplug"
  ./configure --disable-static --prefix=/usr
  make
}

package() {
  cd "${srcdir}/SDL2_mixer-${pkgver}/"

  make DESTDIR="${pkgdir}" install
  install -Dm644 COPYING.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
} 
