# Maintainer: Stefano Avallone <stavallo@gmail.com>

pkgbase=kdeplasma-addons-frameworks-git
pkgname=(kdeplasma-addons-applets-calculator-frameworks-git
 kdeplasma-addons-applets-eyes-frameworks-git
 kdeplasma-addons-applets-notes-frameworks-git
 kdeplasma-addons-applets-timer-frameworks-git
 kdeplasma-addons-applets-quickshare-frameworks-git
 kdeplasma-addons-applets-kimpanel-frameworks-git
 kdeplasma-addons-applets-fuzzy-clock-frameworks-git
 kdeplasma-addons-wallpapers-qmlwallpapers-frameworks-git
 kdeplasma-addons-runners-converter-frameworks-git
 kdeplasma-addons-runners-dictionary-frameworks-git
 kdeplasma-addons-frameworks-git)
pkgver=r6432.0d2adbd
pkgrel=1
pkgdesc="All kind of addons to improve your Plasma experience"
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/kde/kdeplasma-addons'
license=('LGPL')
makedepends=('kdoctools' 'extra-cmake-modules' 'git' 'krunner' 'kdelibs4support' 'kcmutils' 'scim' 'libibus')
source=('git://anongit.kde.org/kdeplasma-addons.git#branch=frameworks')
md5sums=('SKIP')

pkgver() {
  cd kdeplasma-addons
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../kdeplasma-addons \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DQT_PLUGIN_INSTALL_DIR=lib/qt/plugins \
    -DQML_INSTALL_DIR=lib/qt/qml \
    -DBUILD_TESTING=OFF
  make
}

package_kdeplasma-addons-applets-calculator-frameworks-git() {
  pkgdesc='Calculator applet for Plasma'
  depends=('plasma-workspace')
  cd build/applets/calculator
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-applets-eyes-frameworks-git() {
  pkgdesc='XEyes clone for Plasma'
  depends=('plasma-workspace')
  cd build/applets/eyes
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-applets-notes-frameworks-git() {
  pkgdesc='Notes applet for Plasma'
  depends=('plasma-workspace')
  cd build/applets/notes
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-applets-timer-frameworks-git() {
  pkgdesc='Timer applet for plasma'
  depends=('plasma-workspace')
  cd build/applets/timer
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-applets-quickshare-frameworks-git() {
  pkgdesc='Quick share applet for plasma'
  depends=('plasma-workspace')
  cd build/applets
  make DESTDIR="$pkgdir/temp" install
  install -dm755 "$pkgdir"/opt/kf5/share/{kservices5,plasma/plasmoids}
  mv "$pkgdir"/temp/opt/kf5/share/kservices5/plasma-applet-org.kde.plasma.quickshare.desktop "$pkgdir"/opt/kf5/share/kservices5
  mv "$pkgdir"/temp/opt/kf5/share/plasma/plasmoids/org.kde.plasma.quickshare "$pkgdir"/opt/kf5/share/plasma/plasmoids
  rm -r "$pkgdir"/temp
}

package_kdeplasma-addons-applets-kimpanel-frameworks-git() {
 pkgdesc='A generic input method panel for Oriental languages'
 depends=('plasma-workspace')
 optdepends=('scim: SCIM backend' 'fcitx: FCITX backend' 'libibus: IBUS backend')
 cd build/dataengines/kimpanel
 make DESTDIR="$pkgdir" install
 cd $srcdir/build/applets/kimpanel
 make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-applets-fuzzy-clock-frameworks-git() {
  pkgdesc='Time displayed in a less precise format'
  depends=('plasma-workspace')
  cd build/applets/fuzzy-clock
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-wallpapers-qmlwallpapers-frameworks-git() {
  pkgdesc='QML wallpapers for Plasma'
  depends=('plasma-workspace')
  cd build/wallpapers/qmlwallpapers
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-runners-converter-frameworks-git() {
  pkgdesc='Unit conversion runner'
  depends=('plasma-workspace')
  cd build/runners/converter
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-runners-dictionary-frameworks-git() {
  pkgdesc='Dictionary runner'
  depends=('plasma-workspace')
  cd build/runners/dictionary
  make DESTDIR="$pkgdir" install
}

package_kdeplasma-addons-frameworks-git() {
  pkgdesc='All kind of addons to improve your Plasma experience'
  depends=(kdeplasma-addons-applets-calculator-frameworks-git
   kdeplasma-addons-applets-eyes-frameworks-git
   kdeplasma-addons-applets-notes-frameworks-git
   kdeplasma-addons-applets-timer-frameworks-git
   kdeplasma-addons-applets-quickshare-frameworks-git
   kdeplasma-addons-applets-kimpanel-frameworks-git
   kdeplasma-addons-applets-fuzzy-clock-frameworks-git
   kdeplasma-addons-wallpapers-qmlwallpapers-frameworks-git
   kdeplasma-addons-runners-converter-frameworks-git
   kdeplasma-addons-runners-dictionary-frameworks-git)
}
