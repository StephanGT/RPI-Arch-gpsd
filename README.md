# RPI-Arch-gpsd
## Gpsd on Raspberry PI's run under Arch Linux.
Minimal Builds with PPS and NMEA0183 Support for NTP.

Based on the AUR [gpsd-timing](https://aur.archlinux.org/packages/gpsd-timing/) .<br />
Remove the Build in fixed Portspeed. <br />
Set now the Baudrate in /etc/default/gpsd. <br />

Update the Python Libdir Patch to Version 3.nn.

### Sources enabled:
<pre>
* gpsclock
* isync         | U-Blox
* ipv6
* ublox
* usb
* leapfetch
* magic_hat     | Uputronics, U-box M8, PPS @ GPIO18
* mtk3301       | Adafruit Ultimate GPS, PPS @ GPIO4
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
</pre>
