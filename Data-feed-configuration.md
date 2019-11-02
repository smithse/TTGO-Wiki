# Data feed configuration

rdzTTGOsonde can send data to external devices. Currently supported are AXUDP packets sent to aprsmap on a PC, and KISS over TCP/IP for APRSdroid.

_(note: data is currently incomplete and unfiltered. For DFM sonde (which transmits latitude and longitude in different frames), it may temporarily send incomplete (and thus wrong) data, and the time stamp is only updated if a DFM frame contains one (not all frames do). Please do not feed such data to public servers such as aprs.fi or radiosondy.info. Its just fine for your own map on phone or PC)_

## KISS TCP parameters (APRSdroid)
* Set "KISS TNC" to 1 to enable the KISS service on TCP port 14590

In APRSdroid you have to configure
* Connections: TNC (KISS)
* Type of connection: TCP/IP
* Server for TNC TCP/IP: _IP address of ESP32 board_

APRSdroid will connect to the rdzTTGOsonde board and receive all position reports via TCP/IP (AX25 KISS frames)

## AXUDP parameters (aprsmap)
* Set "AXUDP Host" to the IP address of the computer running aprsmap
* Set "AXUDP Port" to some UDP port number, such as 9002
* (Rate limit: currently unused)

rdzTTGOsonde will send all position updates using AXUDP protocol to the configured host and destination port.

On aprsmap you need to configure
Config -> RF Ports -> RF-Port 1 -> ":9001:9002"

_(or RF-Port 2/3/4; the port number at the end must match the value configured in the rdzTTGOsonde config.)_

## APRS parameters
(currently disabled and not used)
* Call
* Passcode
* APRS TCP host
* APRS TCP port
* Rate limit

