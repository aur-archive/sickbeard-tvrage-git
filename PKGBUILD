# Maintainer: Justin Dray <justin@dray.be>

pkgname=sickbeard-tvrage-git
pkgver=r433.dd9a7f6
pkgrel=1
pkgdesc="A PVR application that downloads and manages your TV shows. Echel0n fork with tvrage and torrents support."
arch=('any')
url="https://github.com/echel0n/SickBeard-TVRage"
license=('GPL3')
depends=('python2' 'python2-cheetah')
makedepends=('git')
optdepends=('sabnzbd: NZB downloader'
            'python2-notify: desktop notifications')
options=('!strip')
install=sickbeard.install
conflicts=('sickbeard' 'sickbeard-piratebay-git')
source=("$pkgname::git://github.com/echel0n/SickBeard-TVRage.git"
        'sickbeard-system.service'
        'sickbeard-user.service'
	'sickbeard.tmpfile')
sha256sums=('SKIP'
            'aa2b6496bf622d2b235a47b80d950ba84411e879a08bc656d227e224653aeded'
            'bf2f9792d3d7e1d703fec9bf61a1562a34b8d08d1dba3d560e6299ea25bd5a72'
            '24f20de2445ff3998aad5d87d94e0fea3b22eb1d0a451ed33ec301ac36a7398d')

pkgver() {
	cd $pkgname
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	mkdir -p "$pkgdir/opt/sickbeard"
	chmod 775 "$pkgdir/opt/sickbeard"
	cp -r $pkgname/* "$pkgdir/opt/sickbeard"

	install -D -m644 sickbeard-system.service "$pkgdir/usr/lib/systemd/system/sickbeard.service"
	install -D -m644 sickbeard-user.service "$pkgdir/usr/lib/systemd/user/sickbeard.service"
	install -D -m644 sickbeard.tmpfile "$pkgdir/usr/lib/tmpfiles.d/sickbeard.conf"

	find "$pkgdir" -type d -name '.git' -exec rm -r '{}' +
}

