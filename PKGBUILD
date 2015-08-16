# Maintainer: Edoardo Maria Elidoro <edoardo.elidoro@gmail.com>
# Contributor: Jib <jbc.as (AT) free.fr>
# Last update: 01/27/2011

pkgname=gtk-theme-infinity
_pkgname=infinity-theme
pkgver=1.6.1
pkgrel=2
pkgdesc="Infinity theme for Xfce and Mate."
arch=(any)
license=('GPL')
depends=('gtk-engine-murrine>=0.98')
makedepends=('imagemagick')
optdepends=('slim-theme-infinity: matching theme for slim login manager')
source=(https://launchpad.net/~bisigi/+archive/ppa/+files/infinity-theme_1.6.1.maverick.ppa2+nmu1.tar.gz
        arch-icon-infinity-128.png
        infinity.patch)
url="http://www.bisigi-project.org/?p=1&lang=en"
md5sums=('9a8b75c84a0520b67937bb9df3dd9771'
         'a876d63d76386dacdb569435bfa48127'
		 '39a1a797424ea800635c33fbf3432d90')

package() {
   cd ${srcdir}/${_pkgname}
   # install dirs 
   install -d ${pkgdir}/usr/share/{themes,icons,pixmaps/backgrounds/gnome/other,gnome-background-properties,emerald/themes,doc/bisigi/infinity}
   tar -xzf Gtk/infinity.tar.gz -C Gtk/
   #Icons theme
   echo "Unpacking icons..."
   tar -xjf Icons/infinity.tar.bz2 -C Icons/
   # install arch icons
   local _w=""
   for _w in {16x16,22x22,24x24,32x32}; do
      convert -resize $_w ${startdir}/arch-icon-infinity-128.png Icons/infinity/$_w/places/distributor-logo.png
      convert -resize $_w ${startdir}/arch-icon-infinity-128.png Icons/infinity/$_w/places/gnome-main-menu.png
      convert -resize $_w ${startdir}/arch-icon-infinity-128.png Icons/infinity/$_w/places/start-here.png
   done
   install -D -m644 ${startdir}/arch-icon-infinity-128.png Icons/infinity/scalable/places/distributor-logo.png
   install -D -m644 ${startdir}/arch-icon-infinity-128.png Icons/infinity/scalable/places/gnome-main-menu.png
   install -D -m644 ${startdir}/arch-icon-infinity-128.png Icons/infinity/scalable/places/start-here.png
   #Emerald theme
   mkdir Emerald/infinity
   tar -xzf Emerald/infinity.emerald -C Emerald/infinity
   # install files
   patch  -Np0 <${srcdir}/infinity.patch
   cp -R Gtk/infinity/ ${pkgdir}/usr/share/themes/
   cp -R Icons/infinity/ ${pkgdir}/usr/share/icons
   install -D -m644 Wallpaper/infinity.jpg ${pkgdir}/usr/share/pixmaps/backgrounds/gnome/other
   install -D -m644 Wallpaper/infinity-wallpaper.xml ${pkgdir}/usr/share/gnome-background-properties
   cp -R Emerald/infinity ${pkgdir}/usr/share/emerald/themes/
   install -D -m644 credits.txt ${pkgdir}/usr/share/doc/bisigi/infinity/
}
