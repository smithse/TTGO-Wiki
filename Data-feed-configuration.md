# KISS TNC/AXUDP/AXTCP data feed configuration

rdzTTGOsonde can send data to external devices. Currently supported are AXUDP packets sent to aprsmap on a PC, and KISS over TCP/IP for APRSdroid, and MQTT.  Also supported is APRS over TCP/IP, Chasemapper via JSON/UDP, and Sondehub v2 API.


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

## APRS parameters (for example, for radiosondy.info)

Connects to an aprs server, using call as login
* Passcode: APRS login passcode
* APRS TCP active: 1=enabled, 0=disabled
* APRS TCP host: hostname or IP address, such as radiosondy.info
* APRS TCP port: port number, such as 14580 (aprs standard) or 14590 (radiosondy.info without forward to aprs.fi servers)
* Rate limit: number of seconds between aprs position reports, must be >= 5 for public aprs servers
* APRS object call: if set, object reports use a different source callsigns (APRS login and tracker location beacons are always sent with the main callsign specified above). For wettersonde.net, this is the "Objectcall" (and "Call" is the "Gatecall"). For most other servers, this can be left empty.
* APRS tracker symbol: must be 4 characters. The first two are used for "fixed" mode (Table ID, Symbol Code), the second two are used for "chase" mode. See https://www.aprsdirect.com/symbol/list
* APRS location reporting: configure if/how to send APRS beacons with tracker position: fixed sends receiver fixed position from general configuration, chase sends GPS position (requires GPS), auto switches automatically (GPS fix available and away from fixed position => chase, otherwise fixed)
* APRS location comment: appended to the tracker position beacon

