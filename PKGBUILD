pkgname=sdl2_mixer
pkgver=2.0.0
pkgrel=1
pkgdesc="A simple multi-channel audio mixer"
arch=('x86_64')
url="http://www.libsdl.org/projects/SDL_mixer/"
license=('custom')
depends=('sdl2' 'libvorbis' 'libmikmod' 'smpeg')
makedepends=('fluidsynth')
optdepends=('fluidsynth: MIDI software synth, replaces built-in timidity')
options=('!libtool')
source=("http://192.241.223.99/projects/SDL_mixer/release/SDL2_mixer-$pkgver.tar.gz")
md5sums=('65f6d80df073a1fb3bb537fbda031b50')

build() {
  cd "$srcdir/SDL2_mixer-$pkgver"

  sed -e "/CONFIG_FILE_ETC/s|/etc/timidity.cfg|/etc/timidity++/timidity.cfg|" \
      -e "/DEFAULT_PATH/s|/etc/timidity|/etc/timidity++|" \
      -e "/DEFAULT_PATH2/s|/usr/local/lib/timidity|/usr/lib/timidity|" \
      -i timidity/config.h

  ./configure --prefix=/usr --disable-static
  make
}

package() {
  cd "$srcdir/SDL2_mixer-$pkgver"
  make DESTDIR="$pkgdir" install

  install -Dm644 COPYING.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}