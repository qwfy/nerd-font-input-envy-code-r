# Maintainer: Paul Davis ("dangersalad") <paul@dangersalad.com>
# Old Maintainer: javier dot tia at gmail dot com
# Older Maintainer: onestone at gmail dot com

pkgname=ttf-nerd-fonts-input-envy-code-r
epoch=1
pkgver=2.1.0
pkgrel=2
pkgdesc='Fonts for Code, from Font Bureau, Envy Code R style, patched with nerd-fonts'
arch=('any')
url='http://input.fontbureau.com/'
license=('custom:Font Software License Agreement')
makedepends=('fontforge' 'parallel')
url_long="${url}build/?fontSelection=fourStyleFamily&regular=InputSans-Regular&italic=InputSans-Italic&bold=InputSans-Bold&boldItalic=InputSans-BoldItalic&a=0&g=ss&i=topserif&l=topserif&zero=slash&asterisk=0&braces=0&preset=envy&line-height=1.2&accept=I+do&email="
# go to the input website and try a download to get more info on how to customise this URL. Below are the setting I personally use, the default above matches the ttf-input package (all defaults on the website)
# url_long="${url}build/?fontSelection=whole&a=ss&g=ss&i=serifs_round&l=serifs_round&zero=0&asterisk=height&braces=0&preset=default&line-height=1.2&accept=I+do&email="
source=("Input_Fonts.zip::${url_long}"
        "https://github.com/ryanoasis/nerd-fonts/archive/v${pkgver}.tar.gz")
sha256sums=('8f7889d4667c5a99b047613aa17d62e1ea7117b910ef7ae9f205f769f97b1644'
            'a084ca91a174b547bab4523507824c76aa91ebcf38f9256a4ffd181813f87bd8')

build () {
  mkdir -p ${srcdir}/TTF
  find ${srcdir}/Input_Fonts -name '*.ttf' \
       | parallel fontforge -script ${srcdir}/nerd-fonts-${pkgver}/font-patcher \
       --no-progressbars --careful \
       --complete --outputdir \
       ${srcdir}/TTF {} \;
}

package() {
    mkdir -p ${pkgdir}/usr/share/fonts/TTF
    cp -r ${srcdir}/TTF/* ${pkgdir}/usr/share/fonts/TTF
    chmod 644 ${pkgdir}/usr/share/fonts/TTF/*

    mkdir -p ${pkgdir}/usr/share/licenses/${pkgname}
    cp ${srcdir}/LICENSE.txt ${pkgdir}/usr/share/licenses/${pkgname}
}
