# Maintainer: Danilo Kuehn <dk[at]nogo-software[dot]de>

_name=packer
pkgname=packer-io
pkgver=0.6.0
pkgrel=1
pkgdesc="Packer is a tool for creating identical machine images for multiple platforms from a single source configuration."
url="http://www.packer.io"
arch=('x86_64' 'i686')
license=('MPL2')
makedepends=('unzip')

if test "$CARCH" == i686; then
	source=("${_name}-$CARCH-${pkgver}.zip::https://dl.bintray.com/mitchellh/packer/${pkgver}_linux_386.zip")
	sha256sums=('1c770c5e84565c071eaf779d82a7b1de8e5ca160ebb5b8150f5b534e2577c098')
else
	source=("${_name}-$CARCH-${pkgver}.zip::https://dl.bintray.com/mitchellh/packer/${pkgver}_linux_amd64.zip")
	sha256sums=('3c3c2d5fff21e0ba9aa25a18fcdf8ec04fbbd2f7364c74d843124336d1d7b36c')
fi
noextract=(${source[@]%%::*})

prepare() {
	if [[ -e ${srcdir}/${_name}-${pkgver} ]]; then rm -rf ${srcdir}/${_name}-${pkgver}; fi
	mkdir ${srcdir}/${_name}-${pkgver}
	unzip -o ${_name}-$CARCH-${pkgver}.zip -d ${srcdir}/${_name}-${pkgver}
}

package() {
	install -dm755 "${pkgdir}/usr/bin"

	cd "${srcdir}/${_name}-${pkgver}"

	for file in `ls ${srcdir}/${_name}-${pkgver}`; do
		if [ "$file" == "packer" ]; then
			install -Dm755 "$file" "${pkgdir}/usr/bin/${file}-io"
		else
			install -Dm755 "$file" "${pkgdir}/usr/bin/${file}"
		fi
	done
}
