# General configuration
(In the "**Config**" tab of the web interface)

## Wifi mode (0/1/2/3) (``wifi``)
- 0: Wifi disabled
- 1: Wifi station mode. Connects to AP in background and dynamically obtains an IP address (connection ok: IP address shown in display). Connection is made to a network configured in the WiFi tab/network.txt with best RSSI value. Automatically re-connnects in case of connection failure.
- 2: Wifi AP mode. Creates an access point (AP symbol + IP address 192.168.4.1. shown in display). Clients (PC or phone) gets an IP via DHCP
- 3: Wifi station of AP autoselec. On startup, shows result of network scan on Display and tries connecting to the first available network in network.txt. Does not reconnect in case an established connection later fails. If no network in network.txt is available at startup time, board starts in AP mode. Decoding RS92 is possible only in Wifi mode 3, as ephemeris data is downloaded on startup only in this mode (if an RS92 sonde is active in the configuration on startup)

## Network mDNS name
Offers name-to-IP-address lookup, so you can use http://rdzsonde.local/ (assuming rdzsonde is the configured mDNS name) instead of http://<ip address/ for accessing the TTGO web interface. Works only if the TTGO and your device is on the same local subnet and if your devices/browser supports mDNS discovery.

## FTP server for ephemeris data (RS92 decoder)
A RS92 sonde does not transmit fully decoded GPS position, but only raw GPS data that needs to be transformed into position information using ephemeris data downloaded from the internet. Needs a server that supports anonymous FTP download.

## Debug mode (0/1) (``debug``)
1: On startup, shows some additional informations on screen
(Currently, in any case lots of debug information is sent on the serial console)

## maximum number of QRG entries (``maxsonde``)
Number of entries in the "QRG" tab. Must be less than 50. Must be larger than 0 as well :-)

## Receiver fixed latitude/longitude/altitude (rxlat, rxlon, rxalt)
Static position of the receiver. If the TTGO does not have a GPS receiver (or if the GPS receiver does not have a GPS fix), then this fixed position information is used whenever the TTGO position is needed, such as distance and direction display on the local display, for SondeHub (displaying the receiver location on sondehub.org, for the initial map position of the LiveMap, etc.)
