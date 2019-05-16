# Generic options

## Wifi mode (0/1/2/3) (``wifi``)
- 0: Wifi disabled
- 1: Wifi station mode. Connects to AP in background (connection ok: IP address shown in display). Connection is made to network in network.txt with best RSSI value. Automatically re-connnects in case of connection failure.
- 2: Wifi AP mode. Creates an access point (AP symbol + IP address 192.168.4.1. shown in display). Clients get an IP via DHCP
- 3: Wifi debug mode. On startup, shows result of network scan on Display and lots of debug information on serial console. tries connecting to the first available network in network.txt. Does not reconnect in case an established connection later fails. If not network in network.txt is available at startup time, board starts in AP mode. 

## Debug mode (0/1) (``debug``)
1: On startup, shows some additional informations on screen
(Currently, in any case lots of debug information is sent on the serial console)

## Maxsonde (``maxsonde``)
Number of entries in the "QRG" tab. Must be less than 100. Must be larger than 0 as well :-)

# Spectrum display parameters

## ShowSpectrum (s) (``spectrum``) and Spectrum Timer (``timer``)
If set to a value spectrum > 0, the spectrum mode is started after reboot (otherwise, the scan mode).
If timer=1, the spectrum display will be active only for ``spectrum`` seconds and then automatically switch to scan mode
(exact behaviour might change in future)

## Startfreq (MHz) (``startfreq``)
Starting frequency in MHz, usually 400 MHz

## Bandwidth (kHz) (``channelbw``)
Configuration value for RXBW during spectrum recording (needs additional testing, probably we should (also) set AGCBW?)

## Spectrum MHz marker (``marker``)
Displey MHz values (start, end) in display in spectrum mode

## Spectrum noisefloor (``noisefloor``)
RSSI value at bottom edge of display

# AXUDP parameters
## Host, Port
IP address and port number

## rate limit
has no effect

# APRS TCP parameters
## No functionality implemented yet, so no point editing these parameters

# Receiver parameters (``rs41.*``, ``dfm.*``)
## AGC bandwidth (``.agcbw``)
## RX bandwidth (``.rxbw``)

