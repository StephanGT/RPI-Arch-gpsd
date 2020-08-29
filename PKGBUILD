# Maintainer: Timothy Brown <sysop@timb.us>
# Contributor: Jaroslav Lichtblau <svetlemodry@archlinux.org>
# Contributor: Tom Gundersen <teg@jklm.no>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Giacomo Rizzo <alt@free-os.it>

pkgname=gpsd-minimal-ntp
pkgver=3.21
pkgrel=1
pkgdesc="Minmal GPS daemon and library to support USB/serial GPS devices, for NTP with (RPI_GPIO)-PPS."
provides=('gpsd')
conflicts=('gpsd')
arch=('armv6h' 'armv7h')
url="http://catb.org/gpsd/"
license=('BSD')
depends=('python' 'libusb' 'bluez-libs' 'pps-tools' 'ntp')
makedepends=('scons' 'docbook-xsl' 'python')
backup=('etc/default/gpsd')
source=(https://download.savannah.gnu.org/releases/"${pkgname%%-minimal-ntp}"/"${pkgname%%-minimal-ntp}"-$pkgver.tar.gz
        https://download.savannah.gnu.org/releases/"${pkgname%%-minimal-ntp}"/"${pkgname%%-minimal-ntp}"-$pkgver.tar.gz.sig
        'gpsd.conf')
sha256sums=('65504c3af8d3b0cce3c07405b8815d7730d2d2be2da7d28d275f1a9c57c6fe91'	# gpsd-3.21.tar.gz
            '951b8c2ab5ca8dcc9c388b29fe0cf55f5bd07e9a0b0707671478a6f928918291'	# gpsd-3.21.tar.gz.sig
            'c9e80e58cb2f2e7bfaf5c4bcb5a030af49c0da7c5e378a78a63a4b589f64167b')	# gpsd.conf
validpgpkeys=('EED4A0893DCC705DB309E202CCF29C7238522905') # Gary E. Miller <gem@rellim.com>

build() {
  cd "${pkgname%%-minimal-ntp}"-$pkgver

  export LINKFLAGS="-lpthread ${LDFLAGS}"
  _pythonpath=`python -c "from sysconfig import get_path; print(get_path('platlib'))"`
  scons minimal=yes \
        prefix=/usr \
        mandir=/usr/share/man \
        includedir=/usr/include \
        libdir=/usr/lib \
        sysconfdir=/etc/default \
        bindir=/usr/bin \
        docdir=/usr/share/doc \
        pkgconfig=/usr/lib/pkgconfig \
        sbindir=/usr/bin \
        udevdir=/usr/lib/udev \
        reconfigure=no \
        control_socket=yes \
        controlsend=no \
        dbus_export=yes \
        socket_export=yes \
        passthrough=yes \
        gpsd_group=uucp \
        gpsd_user=root \
        implicit_link=yes \
        shared=yes \
        ipv6=yes \
        leapfetch=yes \
        libgpsmm=yes \
        manbuild=no \
        max_clients=32 \
        max_devices=4 \
        timing=yes \
        ncurses=yes \
        python=yes \
        python_libdir=$_pythonpath \
        systemd=yes \
        gpsd=yes \
        gpsdclients=yes \
        bluez=no \
        usb=yes \
        ntp=yes \
        ntpshm=yes \
        shm_export=yes \
        pps=yes \
        magic_hat=yes \
        timeservice=yes \
        oscillator=yes \
        aivdm=no \
        ashtech=no \
        earthmate=no \
        evermore=no \
        fury=no \
        fv18=no \
        garmin=no \
        garmintxt=no \
        geostar=no \
        gpsclock=yes \
        greis=no \
        isync=yes \
        itrax=no \
        mtk3301=yes \
        navcom=no \
        netfeed=yes \
        nmea0183=yes \
        nmea2000=no \
        ntrip=no \
        oceanserver=no \
        oncore=no \
        rtcm104v2=yes \
        rtcm104v3=yes \
        sirf=no \
        skytraq=no \
        superstar2=no \
        tnt=no \
        tripmate=no \
        tsip=no \
        ublox=yes	
  scons build
}

package() {
  cd "${pkgname%%-minimal-ntp}"-$pkgver

  # Fix path in systemd files
  sed -i 's|local/sbin|bin|' systemd/{gpsd.service,gpsdctl@.service}

  export DESTDIR="${pkgdir}"
  scons install

  install -Dm755 gpsinit -t "${pkgdir}"/usr/bin
  chmod 755 "${pkgdir}"/usr/bin/*

  install -Dm644 "$srcdir/gpsd.conf" "${pkgdir}"/etc/default/gpsd

  install -Dm644 "gpsd.rules" "${pkgdir}"/usr/lib/udev/rules.d/25-gpsd-usb.rules

  install -Dm755 gpsd.hotplug "${pkgdir}"/usr/lib/udev/gpsd.hotplug

  install -Dm644 systemd/gpsd.service "${pkgdir}"/usr/lib/systemd/system/gpsd.service
  install -Dm644 systemd/gpsd.socket "${pkgdir}"/usr/lib/systemd/system/gpsd.socket
  install -Dm644 systemd/gpsdctl@.service "${pkgdir}"/usr/lib/systemd/system/gpsdctl@.service

  install -Dm644 gpsd.php.in "${pkgdir}"/usr/share/"${pkgname%%-timing}"/gpsd.php.in
  install -Dm644 gpsd.php "${pkgdir}"/usr/share/"${pkgname%%-timing}"/gpsd.php

  install -Dm644 COPYING "${pkgdir}"/usr/share/licenses/"${pkgname%%-timing}"/LICENSE
}
