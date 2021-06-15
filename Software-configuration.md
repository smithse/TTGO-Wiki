# Software configuration
(In the "**Config**" tab of the web interface)

## Wifi mode (0/1/2/3) (``wifi``)
- 0: Wifi disabled
- 1: Wifi station mode. Connects to AP in background and dynamically obtains an IP address (connection ok: IP address shown in display). Connection is made to a network configured in the WiFi tab/network.txt with best RSSI value. Automatically re-connnects in case of connection failure.
- 2: Wifi AP mode. Creates an access point (AP symbol + IP address 192.168.4.1. shown in display). Clients (PC or phone) gets an IP via DHCP
- 3: Wifi debug mode. On startup, shows result of network scan on Display and lots of debug information on serial console. tries connecting to the first available network in network.txt. Does not reconnect in case an established connection later fails. If no network in network.txt is available at startup time, board starts in AP mode. 

## Debug mode (0/1) (``debug``)
1: On startup, shows some additional informations on screen
(Currently, in any case lots of debug information is sent on the serial console)

## Maxsonde (``maxsonde``)
Number of entries in the "QRG" tab. Must be less than 100. Must be larger than 0 as well :-)

## Screen config (1=OLED, 2=TFT, 3=TFT[port]).
Selects the screen layout file to be used. (screens1.txt / screens2.txt / screens3.txt; you can also add additional files).

In the standard version, screens1.txt is designed for the small OLED display, screens2.txt for the TFT display in landscape format, and screens3.txt for the TFT in portrait format. Note that this setting only selects the layout (which information is placed where on the display). The type of display and its orientation is defined in the hardware config.  Make sure to select a screen file that fits to your hardware config!

(Selecting a different config probably requires rebooting the TTGO.)

## Display screens
Defines which screens from the screen layout file should be used. On the left, all entries from the screens#.txt file are shown. Enter a list of numbers. The first number should be a "Scan" layout. After that, you can put a sequence of numbers corresponding to screens you can cycle through with a button.

# Spectrum display parameters

## ShowSpectrum (s) (``spectrum``)
If set to a value spectrum >= 0, the spectrum mode is started after reboot (otherwise, the scan mode).
If spectrum > 0, the spectrum display will be active only for ``spectrum`` seconds and then automatically switch to scan mode
Set to -1 to disable spectrum display

## Startfreq (MHz) (``startfreq``)
Starting frequency in MHz, usually 400 MHz

## Bandwidth (kHz) (``channelbw``)
Configuration value for RXBW during spectrum recording (needs additional testing, probably we should (also) set AGCBW?)

## Spectrum MHz marker (``marker``)
Display MHz values (start, end) in display in spectrum mode

## Spectrum noisefloor (``noisefloor``)
RSSI value at bottom edge of display


