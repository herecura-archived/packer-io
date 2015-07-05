# Maintainer: Danilo Kuehn <dk[at]nogo-software[dot]de>

_name=packer
pkgname=packer-io
pkgver=0.5.2
pkgrel=4
pkgdesc="Packer is a tool for creating identical machine images for multiple platforms from a single source configuration."
url="http://www.packer.io"
arch=('x86_64' 'i686')
license=('MLP2')
makedepends=('unzip')
optdepends=()
conflicts=('packer')

if test "$CARCH" == i686; then
	source=("${_name}-$CARCH-${pkgver}.zip::https://dl.bintray.com/mitchellh/packer/${pkgver}_linux_386.zip")
	sha256sums=('114b6ea3c623a048552d1464a34866f6d9738a3a5dcf62e606ced60c8958619f')
else
	source=("${_name}-$CARCH-${pkgver}.zip::https://dl.bintray.com/mitchellh/packer/${pkgver}_linux_amd64.zip")
	sha256sums=('813f856a3d326d2a65f561edac8050d981f93ea51da03b0fb6b3d72010a5fc96')
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
		install -Dm755 "$file" "${pkgdir}/usr/bin/${file}"
	done
}
