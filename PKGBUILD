# Maintainer: Posi<posi1981@gmail.com>
pkgname=betterbird-esr-bin
_pkgname=betterbird
pkgver=128.3.1esr
_build=bb12
pkgrel=1
pkgdesc="GERMAN // Betterbird is a fine-tuned version of Mozilla Thunderbird, Thunderbird on steroids, if you will."
arch=('x86_64')
url="https://www.betterbird.eu/index.html"
license=('MPL2')
depends=('dbus-glib' 'hunspell')
optdepends=('hunspell-en_US' 'hunspell-de')
provides=("betterbird=${pkgver}")
conflicts=('betterbird')
source=(
    "https://www.betterbird.eu/downloads/128-Preview/${_pkgname}-${pkgver//_/-}-${_build}.en-US.linux-x86_64.tar.bz2"
    "betterbird.desktop"
    "vendor-prefs.js"
)

package() {
    install -d "${pkgdir}/opt"
    install -d "${pkgdir}/usr/bin"
    install -d "${pkgdir}/usr/share/applications"

    cp -r "${srcdir}/${_pkgname}/" "${pkgdir}/opt/${_pkgname}"
    install -m644 "${srcdir}/${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
    install -m644 "${srcdir}/vendor-prefs.js" -t "${pkgdir}/opt/${_pkgname}/defaults/pref"
    ln -s /opt/$_pkgname/betterbird "$pkgdir"/usr/bin/$_pkgname
    ln -s /usr/share/hunspell "${pkgdir}/opt/${_pkgname}/dictionaries"

    echo     "

	  >>>>>    Bitte nicht vergessen eine Stimme für dieses Paket abzugeben. DANKE
	  >>>>>    https://aur.archlinux.org/packages/betterbird-de-bin

	  >>>>> THIS IS THE ESR VERSION: THERE IS NO GERMAN VERSION.
	  >>>>> DOWNLOAD THE LANGUAGE XPI HERE: https://www.betterbird.eu/downloads/get.php?os=all&lang=de&version=future
	  "

    #icons
    for i in 16 22 24 32 48 64 128 256; do
        install -d "$pkgdir"/usr/share/icons/hicolor/${i}x${i}/apps/
        ln -s /opt/$_pkgname/chrome/icons/default/default$i.png \
            "$pkgdir"/usr/share/icons/hicolor/${i}x${i}/apps/$_pkgname.png
    done
}
sha256sums=('5d46cc5fcd1c3b5ed73d304c46c708350c8d3097e5fa73c04258d8ef62d4a889'
            'b664d5453512ba1c8a58699d106fb1248991dbae0ee44464484be0886278945b'
            'b11745416d2b2f8bac1ccd3dcb99411c7239b067adf9eb973903c448f8747d09')

