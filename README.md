# RPI-Arch-gpsd
## Gpsd on Raspberry PI's run under Arch Linux.
Minimal Builds with PPS and NMEA0183 Support for NTP.

Basiert auf dem  AUR [gpsd-timing](https://aur.archlinux.org/packages/gpsd-timing/) .<br />
Die 'fixed Portspeed' Funktion wird nicht mehr mit eingebaut. Die Baudrate kann nun in /etc/default/gpsd anpasst werden. <br />

Update des Python Libdir Patches für Version 3.21.

### Sources enabled:

* gpsclock
* isync &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | U-Blox
* ipv6
* ublox
* usb
* leapfetch
* magic_hat &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Uputronics, U-box M8, PPS @ GPIO18
* mtk3301 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Adafruit Ultimate GPS, PPS @ GPIO4
* ntp
* ~~ntrip~~
* ntpshm
* nmea0183
* oscillator
* pps
* rtcm104v2
* rtcm104v3
* shm_export
* timing
* timeservice
