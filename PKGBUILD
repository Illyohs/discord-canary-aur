# Maintainer: Cayde Dixon <me@cazzar.net>
# Co-Maintainer: Anthony Anderson <aantony4122@gmail.com>

pkgname=discord-canary
pkgver=0.0.8
pkgrel=1
pkgdesc='Discord Canary linux release'
arch=('x86_64')
url='https://discordapp.com/'
provides=('discord-canary')
license=('custom')
depends=('gtk2' 'gconf' 'libnotify' 'libxss')
optdepends=('freetype2-infinality: If you have black screens with emojis install this.')

source=(DiscordCanary.desktop LICENSE DiscordCanary.sh)
source_x86_64=("https://cdn-canary.discordapp.com/apps/linux/${pkgver}/discord-canary-${pkgver}.tar.gz") #This is always latest build, right now I do not know of a version param.
sha256sums=('04120aec68647be5de5689ead51ba3fc976ada3cf6616144b97d2b75e0782eae'
            '688f418cd32a682c6d331c211fedd48ff86ee8ba5a7640f589eadb32996af80f'
            '912cb31b21023980614437b859bb11f39697108c0e9ca21778f81da8065a0815')
sha256sums_x86_64=('7362afababed47a6c6ec114a755fdeccce247fe5de37a2e55bdb5dae639788bc')

package() {
  # Install the main files.
  install -d "${pkgdir}/opt/${pkgname}"
  cp -a "${srcdir}/DiscordCanary/." "${pkgdir}/opt/${pkgname}"

  # Exec bit
  chmod 755 "${pkgdir}/opt/${pkgname}/DiscordCanary"


  # Desktop Entry
  install -d "${pkgdir}/usr/share/applications"
  install "${srcdir}/DiscordCanary.desktop" "${pkgdir}/usr/share/applications"

  # Main binary
  install -d "${pkgdir}/usr/bin"
  #ln -s "/opt/${pkgname}/DiscordCanary" "${pkgdir}/usr/bin/DiscordCanary"
  #installing from .sh due to how the tar extracts.
  install "${srcdir}/DiscordCanary.sh" "${pkgdir}/usr/bin/DiscordCanary"

  # Create symbolic link to the icon
  install -d "${pkgdir}/usr/share/pixmaps"
  ln -s "/opt/${pkgname}/discord.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"

  # License
  install -Dm644 "${srcdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
