# Maintainer: Posi<posi1981@gmail.com>
pkgname=betterbird-esr-de-bin
_pkgname=betterbird
pkgver=128.3.2esr
_build=bb13
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
    "de-languagepack.xpi::https://www.betterbird.eu/downloads/get.php?os=all&lang=de&version=future"
)

build() {
    _langpackid="$(grep \"id\" manifest.json | awk -F\" '{print $4}')"
    export _langpackid
}

package() {
    install -d "${pkgdir}/opt"
    install -d "${pkgdir}/usr/bin"
    install -d "${pkgdir}/usr/share/applications"

    cp -r "${srcdir}/${_pkgname}/" "${pkgdir}/opt/${_pkgname}"
    install -m644 "${srcdir}/${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
    install -m644 "${srcdir}/vendor-prefs.js" -t "${pkgdir}/opt/${_pkgname}/defaults/pref"
    ln -s /opt/$_pkgname/betterbird "$pkgdir"/usr/bin/$_pkgname
    ln -s /usr/share/hunspell "${pkgdir}/opt/${_pkgname}/dictionaries"

    echo "

	  >>>>>    Bitte nicht vergessen eine Stimme für dieses Paket abzugeben. DANKE
	  >>>>>    https://aur.archlinux.org/packages/betterbird-de-bin

	  "

    #icons
    for i in 16 22 24 32 48 64 128 256; do
        install -d "$pkgdir"/usr/share/icons/hicolor/${i}x${i}/apps/
        ln -s /opt/$_pkgname/chrome/icons/default/default$i.png \
            "$pkgdir"/usr/share/icons/hicolor/${i}x${i}/apps/$_pkgname.png
    done

    # german language pack
    install -D -m644 "de-languagepack.xpi" "${pkgdir}/opt/betterbird/extensions/${_langpackid}.xpi"
}
sha256sums=('71f6a6efa28d55db39f4563fa457edbf872ef736ac8c7cab2886c114ccb5b5fb'
            'b664d5453512ba1c8a58699d106fb1248991dbae0ee44464484be0886278945b'
            'b11745416d2b2f8bac1ccd3dcb99411c7239b067adf9eb973903c448f8747d09'
            '2595f72afd32404432ac39b3568391e05319c4665e8080bfb304e55e424082f1')
