# Maintainer: Chipster Julien <julien dot chipster @ archlinux dot fr>
pkgname=weather_daemon
url="https://github.com/Chipsterjulien/weather_daemon"
pkgver=0.2
pkgrel=6
pkgdesc="Daemon that can download weather forecast on wunderground"
arch=('any')
license=('GPL')
depends=(python python-yaml python-requests)
md5sums=('a7def1c3ce8483ea31379ff15fb5af54')
source=($pkgname-$pkgver.tar.gz)

install=weather.install

build()
{
	echo "nothing to do"
	# nothing to do
}

package()
{
	# Create directories
	cd "$srcdir/$pkgname-$pkgver"
	mkdir -p "$pkgdir/etc"
	mkdir -p "$pkgdir/usr/bin"
	mkdir -p "$pkgdir/usr/lib/systemd/system"
	mkdir -p "$pkgdir/var/log/weather_daemon"
	mkdir -p "$pkgdir/usr/share/fonts/truetype/weather_daemon/"
	mkdir -p "$pkgdir/usr/share/weather_daemon/icons/"
  
    # Create group and weather_daemon user
  
    getent group weather_daemon &>/dev/null || groupadd -r -g 465 weather_daemon >/dev/null
	getent passwd weather_daemon &>/dev/null || useradd -r -u 465 -g weather_daemon -d /tmp -s /bin/bash >/dev/null weather_daemon
    
	# copy
	
	cp -a weather_daemon.py "$pkgdir/usr/bin/weather_daemon"
	cp -a weather_daemon_example.conf "$pkgdir/etc"
	cp -a systemd "$pkgdir/usr/lib/systemd/system/weather_daemon.service"
	cp -a fonts/* "$pkgdir/usr/share/fonts/truetype/weather_daemon/"
	cp -a icons/* "$pkgdir/usr/share/weather_daemon/icons/"

	# Fixing right

	chmod 644 "$pkgdir/etc/weather_daemon_example.conf"
	chmod 755 "$pkgdir/var/log/weather_daemon"
	chmod 755 "$pkgdir/usr/bin/weather_daemon"
}
