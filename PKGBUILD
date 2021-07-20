# Maintainer: carstene1ns <arch carsten-teibes de> - http://git.io/ctPKG

pkgname=easyrpg-player-git
pkgver=0.6.2.r1294.g8666a3b53
pkgrel=1
pkgdesc="FLOSS RPG Maker 2000/2003 and EasyRPG games interpreter (development version)"
arch=('i686' 'x86_64')
url="https://easyrpg.org"
license=('GPL3')
conflicts=("${pkgname%-*}")
provides=("${pkgname%-*}=${pkgver%.r*}")
makedepends=('git' 'asciidoc')
depends=('liblcf-git' 'pixman' 'freetype2' 'libvorbis' 'mpg123'
         'libsndfile' 'speexdsp' 'wildmidi' 'fmt')
optdepends=('wine: for installing the run time packages (RTP)'
            'libxmp: decoder for tracker music, used by few games'
            'alsa-lib: native MIDI playback'
            'fluidsynth: another MIDI decoder'
            'rpg2000-rtp: run time package for some 2k games'
            'rpg2003-rtp: run time package for some 2k3 games')
install=$pkgname.install
source=(${pkgname%-*}::"git+https://github.com/EasyRPG/Player.git")
md5sums=('SKIP')

pkgver() {
  cd ${pkgname%-*}
  git describe --long | sed 's/-/.r/;s/-/./'
}

build () {
  cd ${pkgname%-*}

  autoreconf -i
  ./configure --prefix=/usr --enable-fmmidi
  make
}

package () {
  make -C ${pkgname%-*} DESTDIR="$pkgdir/" install
}
