# Contributor: saik0
# Maintainer: Leios <jrs0037@auburn.edu>
pkgname=boson-x
pkgver=1.0.5
_pkgver=${pkgver//\./_} # replace all '.' with '_'
pkgrel=3
pkgdesc="DRM-free rotational running game"
arch=('x86_64' 'i686')
url="http://www.boson-x.com/"
license=('Custom')
source=("http://downloads.muandheyo.com/BosonX_v1_0_5_Linux.zip"
		'bosonx.sh'
		"${pkgname}.desktop")
depends=('mesa')
sha1sums=('4f9511cad328c94cf7d49599ab014f29134448be'
          'a2ad55adce9bef502c0fcb83f1da7646d8822099'
          '97dadb126a3bf8a6868e3e398952997e31537767')

package() {
  cd "${srcdir}/BosonX_v${_pkgver}_Linux/"

  # Executable
if test "$CARCH" == x86_64; then 
  install -Dm755 bosonx64 \
  	"${pkgdir}/usr/share/${pkgname}/bosonx"
else
  install -Dm755 bosonx32 \
  	"${pkgdir}/usr/share/${pkgname}/bosonx"
fi

  # Desktop File
  install -Dm755 "${srcdir}/${pkgname}.desktop" \
	"${pkgdir}/usr/share/applications/${pkgname}.desktop"

  # Icon
  install -Dm644 data/bosonx_symbol.png_ ${pkgdir}/usr/share/pixmaps/${pkgname}.png

  # Game data
  install -d "${pkgdir}/usr/share/${pkgname}/"
  cp -rd --no-preserve=ownership data/ "${pkgdir}/usr/share/${pkgname}/data"

  # bosonx executable wants to be in the same directory as 'data/'
  # Symbolic links aren't currently working.
  install -Dm755 ${srcdir}/bosonx.sh "${pkgdir}/usr/bin/${pkgname}"
  

  # License
  install -Dm644 LICENSES.txt \
  	"${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
