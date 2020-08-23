# RPI-Arch-gpsd
## Gpsd on Raspberry PI's run under Arch Linux.
Minimal Builds with PPS and NMEA0183 Support for NTP.

Based on the AUR [gpsd-timing](https://aur.archlinux.org/packages/gpsd-timing/).
Remove the Build in fixed Portspeed.
Set now the Baudrate in /etc/default/gpsd.

Update the Python Libdir Patch to Version 3.21.

### Sources enabled:

* gpsclock
* isync
* ipv6
* ublox
* usb
* leapfetch
* magic_hat
* mtk3301
* ntp
* ntrip
* ntpshm
* nmea0183
* oscillator
* pps
* shm_export
* timing
* timeservice
